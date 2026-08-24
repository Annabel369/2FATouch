# 🟩 Creeper Auth v6.3.3 - Cofre Físico com YubiKey

Este projeto transforma um módulo ESP32 com tela touch (CYD - *Cheap Yellow Display*) em um **Autenticador 2FA físico** inspirado no Creeper (Minecraft). O sistema exige um toque físico em uma **YubiKey** para validar o acesso, abrindo mecanicamente a cabeça do Creeper através de um Servo Motor e acendendo uma luz interna via Relé.

---

## 🛠️ Hardware Utilizado

*   **Placa:** ESP32-2432S028R (conhecida como CYD - Cheap Yellow Display).
*   **Mecânica:** Servo Motor (ex: SG90 ou MG90S) atuando como braço mecânico para abrir a cabeça.
*   **Iluminação:** Módulo Relé acionando uma lâmpada/abajur.
*   **Segurança:** YubiKey (configurada com slot de *Challenge-Response*).

---

## ⚠️ Dicas Cruciais de Hardware (Para a placa CYD)

A placa **ESP32-2432S028R** possui muitos componentes internos (tela, SD, touch, áudio) que ocupam a maioria dos pinos nativos do ESP32. Para evitar queima de componentes ou conflitos (como tela branca ou som chiando), siga estas regras rígidas:

### 1. Pinagem Segura (Conector Traseiro P3)
Nunca use o pino `26` nesta placa para hardware externo, pois ele é permanentemente ligado ao DAC (áudio). 
Na parte traseira da placa, localize o conector branco de 4 pinos (geralmente rotulado como **P3**). Ele expõe dois pinos perfeitamente seguros para uso:
*   **GPIO 22:** Usado para o sinal do Módulo Relé (Luz).
*   **GPIO 27:** Usado para o sinal PWM do Servo Motor.

### 2. Alimentação de Energia (O "Pulo do Gato")
O conector **P3** fornece apenas **3.3V**. Se você ligar o Servo Motor ou o Relé diretamente no `VCC` do P3, eles vão "tremer", travar ou reiniciar o ESP32 por falta de corrente elétrica.
*   **Sinal (Dados):** Ligue os fios Amarelo/Laranja (sinal) do Servo e do Relé nos pinos **22 e 27** do P3.
*   **Energia (5V):** Puxe os fios Vermelho (VCC) e Preto (GND) do seu Servo/Relé diretamente do conector **P1** (perto da porta USB), que fornece **5V nativos**, ou solde diretamente no pino `VBUS` da entrada USB. 

---

## 💻 Dependências de Software

Para o Servo Motor funcionar na arquitetura ESP32 sem dar erro de compilação (conflito de *timers* `LEDC_MAX_BIT_WIDTH`), **NÃO utilize a biblioteca padrão `Servo.h` do Arduino.**

1. Vá no **Gerenciador de Bibliotecas** da IDE do Arduino.
2. Busque e instale a biblioteca: **`ESP32Servo`** (por Kevin Harrington, John K. Bennett).
3. No código, a configuração inicial deve ser feita assim:

```cpp
#include <ESP32Servo.h> 

Servo servoCreeper;
const int PINO_RELE_LUZ = 22; 
const int PINO_SERVO = 27;    

void setup() {
  // Ajuste de timers do ESP32 para o Servo
  ESP32PWM::allocateTimer(0);
  ESP32PWM::allocateTimer(1);
  ESP32PWM::allocateTimer(2);
  ESP32PWM::allocateTimer(3);
  
  servoCreeper.setPeriodHertz(50); // Frequência de 50Hz
  servoCreeper.attach(PINO_SERVO, 500, 2400); 
  servoCreeper.write(0); // Inicia fechado
}
```

---

## 🔒 Como Funciona a Automação YubiKey

O sistema não abre a porta com um simples comando web aberto. Ele exige uma senha combinada validada fisicamente pelo hardware.

1. **Espera de Toque:** Um script em Python (`testa_yubikey_ykman.py`) roda no PC local e "trava" aguardando o toque capacitivo na YubiKey física.
2. **Disparo da Requisição:** Após validar o desafio localmente, o PC dispara um comando HTTP GET silencioso para o ESP32 passando a credencial secreta:
   ```http
   GET http://<IP_DO_CREEPER>/aprovado?senha=SuaSenhaAqui
   ```
3. **Ação do ESP32:** O ESP32 recebe a requisição e valida a senha. Se estiver correta:
   * 🖼️ Carrega a imagem do SD Card e exibe a mensagem de sucesso na tela.
   * 💡 Aciona o Relé (GPIO 22) para acender a luz interna.
   * ⚙️ Gira o Servo Motor (GPIO 27) para 90 graus, abrindo a cabeça mecanicamente.
4. **Fechamento Automático:** O loop principal do ESP32 monitora o tempo. Exatamente **30 segundos** após a abertura, ele corta a energia do Relé, retorna o Servo para 0 graus e volta o display para o rosto padrão do Creeper.
