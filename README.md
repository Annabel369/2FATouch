<img width="229" height="76" alt="image" src="https://github.com/user-attachments/assets/e4cbc7b1-96ca-43fa-ad09-fae37f71b348" />
![WIN_20260106_03_42_48_Pro](https://github.com/user-attachments/assets/9bae5c3f-6ea4-4f8b-a3c6-ab38e6009a8d)

<img width="1040" height="503" alt="image" src="https://github.com/user-attachments/assets/07b3348c-3310-44e3-be96-e2cc8f625813" />
ESP32-2432S028R

https://github.com/user-attachments/assets/b97c8798-70a3-4e39-a5d2-1c58f077c853

# dependencie 
https://github.com/Annabel369/ESP32FTPServer


Arquivo de configuração para a biblioteca TFT_eSPI. Precisa ser colocado no diretório onde a biblioteca está instalada.

lv_conf.h
Arquivo de configuração da biblioteca LVGL. Precisa ser colocado no diretório de bibliotecas do Arduino.

Fonte: https://randomnerdtutorials.com/lvgl-cheap-yellow-display-esp32-2432s028r/

DNS NAME IPV6 se nao  so pelo ipv4

http://creeper.local/

<img width="1244" height="565" alt="image" src="https://github.com/user-attachments/assets/13e27c97-57c9-4a0f-b830-3d750f9c219d" />

    // 6. Verificação de Dispositivos IPv6 Específicos (Mickey's Devices)
    // Basta adicionar o IPv6 completo que aparece no Serial entre as aspas
    if (clientIP == "fe80::seu_ipv6_pc_aqui" || 
        clientIP == "fe80::seu_ipv6_celular_aqui" || 
        clientIP == "fe80::seu_ipv6_tablet_aqui" || 
        clientIP == "fe80::seu_ipv6_note_aqui") {
      Serial.println("Acesso Liberado: Dispositivo IPv6 Reconhecido");
      return true;
    }



https://github.com/Annabel369/PanelMinecraft/blob/main/User_Setup.h
#Copy the User_Setup.h file provided earlier and replace the existing file.
<img width="786" height="675" alt="image" src="https://github.com/user-attachments/assets/77f1cb7a-b2fc-4b38-a4ad-369ca865f97d" />

Procura algum projeto de impressoar 3d que simule o projeto original do creeper do Cinepolis 

https://www.crealitycloud.com/pt/model-detail/minecraft-creeper-printing-model?source=5



# 🟢 Creeper Auth v7.2.2 - Dual Stack & Crypto Vault
O Creeper Auth v5.5 é um dispositivo de segurança de hardware baseado no ESP32. Ele combina um autenticador 2FA (TOTP) físico, um cofre de chaves mestras (Seeds) e um sistema de segurança de rede híbrido (IPv4/IPv6). Tudo isso com uma interface temática do Minecraft e gerenciamento total via SD Card e Web.

# 🚀 Novidades da Versão v7.2.2
Suporte Dual-Stack: Agora opera em IPv4 e IPv6 simultaneamente.

Whitelist Dinâmica: Novo Agente Python que monitora sua rede e autoriza seu PC automaticamente.

Cofre de Seeds 3.0: Visualização de frases de recuperação (12/24 palavras) em 3 colunas numeradas no visor.

Gestão de Rede via Web: Altere Wi-Fi e IPs de segurança sem precisar mexer no código ou no SD.

Interface Colorida: Sistema de gerenciamento com botões coloridos para evitar exclusões acidentais.

# 💻 O Agente de Segurança (Python)
Para que as funções de Adicionar, Editar e Excluir funcionem, você deve rodar o Agente Python no seu computador. Ele funciona como uma "chave digital" que avisa ao Creeper que você é o dono legítimo do dispositivo.

# 🛠️ Pré-requisitos do Sistema
Para o reconhecimento de rede funcionar, o Python precisa de acesso de baixo nível à placa de rede:

Instalar Npcap 1.85: * Baixe e instale o Npcap 1.85.

Importante: Durante a instalação, marque a opção "Install Npcap in WinPcap API-compatible Mode".

Instalar Python 3.x: Certifique-se de que o Python está no seu PATH.

Bibliotecas Python: O script usa bibliotecas nativas, mas para scanners avançados, você pode precisar:

Bash

pip install scapy
# 🛠️ Hardware Necessário
ESP32 (30 pinos).

Display TFT 2.4" (ILI9341 ou ST7789).

Módulo Cartão Micro SD (SPI).

Cartão Micro SD (Formatado em FAT32).

# 📚 Bibliotecas do Arduino (IDE)
TFT_eSPI: (Configurar User_Setup.h para os pinos do seu display).

NTPClient e WiFiUdp.

ESP32FtpServer: Para acesso remoto aos arquivos.

mbedtls: (Nativa do ESP32).

# ⚙️ Configuração Inicial
Insira o cartão SD no PC e crie um arquivo config.txt:

Plaintext

SSID=SuaRedeWifi
PASS=SuaSenha
MODO=REDE
IP_ALVO=192.168.100.
O Creeper iniciará e mostrará o IPv4 e o IPv6 na tela.

<img width="1504" height="575" alt="image" src="https://github.com/user-attachments/assets/85b3c213-bd00-45fe-8296-be44f813e2b7" />


Execute o script agente_creeper.py no seu PC para liberar o acesso ao painel administrativo.

# 📂 Estrutura de Arquivos no SD
/config.txt: Armazena Wi-Fi e regras de IP.

/totp_secrets.txt: Armazena tokens (Nome=Secret=Senha).

/seeds.txt: Armazena frases de recuperação (Nome|Palavras).

# 🛡️ Segurança e Dicas
Backup: O cartão SD é o único lugar onde seus dados moram. Faça cópias periódicas dos arquivos .txt.

Acesso Negado: Se você vir esta mensagem na Web, certifique-se de que o Agente Python está rodando e que o IP do seu PC foi detectado por ele.

Visualização de Seeds: No cofre, as palavras são numeradas de 1 a 24 e organizadas em 3 colunas no display para facilitar a digitação em carteiras como MetaMask ou Ledger.

<img width="629" height="589" alt="image" src="https://github.com/user-attachments/assets/243d8eeb-8935-4c58-8e77-f56b20226d0e" />
exemplo 192.168.100.38,192.168.100.190,aa80::aa94:32aa:e867:623

ou tapar acesso a todos da intranet da casa ou empresa

<img width="391" height="466" alt="image" src="https://github.com/user-attachments/assets/8397a82f-05fd-4969-8b73-1cd4b8710e93" />

# FTP Acesso voce consegue guardar coisas e apaga e tira (mas nao tem acesso aos arquivos Originais gerado pelo sistema



ftp://creeper:1234@192.168.100.49/

<img width="1191" height="327" alt="image" src="https://github.com/user-attachments/assets/c1a8d30b-6931-47af-a48e-48e8c2db86a6" />




# 📄 Licença
Projeto desenvolvido para uso pessoal e entusiastas de segurança e Minecraft. Use com responsabilidade e mantenha seus backups em dia!

<img width="1109" height="970" alt="image" src="https://github.com/user-attachments/assets/80c89aca-2570-4485-b574-4aa815d71cb5" />
# 🟩 Creeper Auth v7.2.2 - Cofre Físico com YubiKey

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

5. # 🛒 Guia de Peças e Hardware (Mecânica e Automação)

Abaixo está a lista completa dos componentes físicos necessários para montar a mecânica do Creeper (abertura da cabeça, iluminação) e a automação da porta secreta.

---

## 1. Módulo Relé (Para a Luz e a Trava)
Para conectar diretamente no pino da placa CYD (ESP32), o ideal é usar um relé que funcione bem com sinais lógicos de **3.3V**.

*   **O que buscar nas lojas:** `Módulo Relé 1 Canal 3.3V Optoacoplado` ou `Módulo Relé 3V Arduino`.

> 💡 **Dica:** Módulos de relé de 5V com "Optoacoplador" geralmente também funcionam se você ligar os 5V no pino `VCC` e o sinal de 3.3V (do ESP32) no pino `IN`. Porém, optar pelo módulo de 3.3V nativo é mais seguro e evita problemas de tensão.

---

## 2. O Motor (Braço Mecânico)
Para levantar a cabeça do Creeper ou abrir a porta, você não precisará de um braço robótico inteiro. Apenas um Servo Motor forte e uma haste metálica já resolvem o problema de forma limpa e escondida.

*   **O Motor:** Busque por `Micro Servo MG90S`. 
    *   *Nota:* A sigla "MG" significa *Metal Gear* (engrenagens de metal). **Não compre** o modelo SG90 azul (de plástico), pois suas engrenagens podem espanar ou quebrar com o peso contínuo da cabeça do Creeper.
*   **A Haste (O "braço"):** Busque por `Tirante para aeromodelo` ou `Pushrod RC`. É um arame fino e resistente de aço com um terminal (*Linkage Stopper*) que se prende na hélice do servo motor e empurra/puxa a tampa do Creeper.

---

## 3. Trava de Porta (Fechadura Secreta)
Para automatizar a porta secreta do quarto com segurança e estética embutida, a melhor opção são as travas tipo solenoide.

*   **O que buscar nas lojas:** `Mini Trava Eletromagnética Solenoide 12V` ou `Fechadura Solenoide Lingueta 12V`.

> ⚡ **Aviso de Energia:** Estas travas puxam muita corrente (Amperes) e operam em **12 Volts**. O seu ESP32 NÃO consegue alimentá-las diretamente. Será necessário o uso de uma fonte de energia 12V externa ligada à tomada. O Módulo Relé atuará apenas como o "interruptor" para liberar essa energia.

### 🔌 Diagrama de Ligação (Trava Solenoide)

1. **Fonte 12V:** Ligada à tomada da parede.
2. **Caminho do Positivo:** O fio positivo (+12V) da fonte entra no Relé pelo borne **`COM`** (Comum) e sai pelo borne **`NO`** (Normally Open / Normalmente Aberto), indo até o fio positivo da trava solenoide.
3. **Caminho do Negativo:** O fio negativo (GND) da trava liga diretamente no fio negativo da fonte 12V.

🎯 **Ação Final:** Quando a YubiKey for tocada e validada, o ESP32 abrirá a cabeça do Creeper e ativará o Relé. O circuito do relé se fecha, permitindo a passagem dos 12V que puxarão a lingueta metálica da trava, destrancando a porta secreta instantaneamente!
