# Projeto Energize: Otimização e Monitoramento do Consumo de Energia

## Descrição

O **Energize** é uma plataforma inovadora projetada para monitorar, analisar e otimizar o consumo de energia elétrica, promovendo eficiência e sustentabilidade. Este projeto utiliza um dispositivo baseado no **ESP32**, que captura dados em tempo real sobre corrente, tensão e potência elétrica. Combinando hardware e software, o sistema integra sensores inteligentes com a plataforma **Thinger.io** para visualização e análise dos dados coletados.

---

## Funcionalidades

- **Monitoramento em Tempo Real**: Leitura de corrente, tensão e potência elétrica diretamente de sensores conectados ao ESP32.
- **Protocolo MQTT**: Utilização do **Thinger.io** como gateway para enviar e gerenciar os dados em tempo real.
- **Conexão Wi-Fi**: Comunicação direta com a plataforma **Thinger.io** para envio e armazenamento dos dados.
- **Facilidade de Configuração**: Código simples e modular para leitura de sensores e configuração Wi-Fi.
- **Segurança e Confiabilidade**: Reconexão automática em caso de falha na conexão Wi-Fi.

---

## Requisitos

### Hardware

- **ESP32**: Microcontrolador usado para coleta e processamento dos dados.
- **Sensores de Corrente**: Para monitorar o consumo de energia.
- **Fonte de Alimentação**: Compatível com o ESP32.
- **Cabo Micro USB**: Para conexão com o computador durante o upload do código.

### Software

- **Plataforma Arduino IDE** (ou outra IDE compatível, como o PlatformIO).
- **Bibliotecas Necessárias**:
  - `WiFi.h`
  - `PubSubClient.h`
  - `ArduinoJson.h`
  - `ThingerESP32.h`

---

## Configuração

1. **Clone o Repositório**
   ```bash
   git clone https://github.com/seu-usuario/energize.git
   cd energize
   ```

2. **Instale as Bibliotecas**
   Abra a Arduino IDE, vá para **Sketch** > **Incluir Biblioteca** > **Gerenciar Bibliotecas...** e procure por:
   - **WiFi**
   - **PubSubClient**
   - **ArduinoJson**
   - **ThingerESP32**

3. **Atualize as Credenciais**
   No arquivo principal, insira suas credenciais de Wi-Fi e da plataforma **Thinger.io**:
   ```cpp
   const char* ssid = "SEU_SSID";           // Nome da sua rede Wi-Fi
   const char* password = "SUA_SENHA";     // Senha do Wi-Fi
   #define USERNAME "SEU_USERNAME"         // Usuário no Thinger.io
   #define DEVICE_ID "SEU_DEVICE_ID"       // ID do dispositivo no Thinger.io
   #define DEVICE_CREDENTIAL "SUA_CREDENCIAL" // Credencial do dispositivo
   ```

4. **Conecte o ESP32 ao Computador**
   Use um cabo Micro USB para conectar o ESP32 ao computador.

5. **Compile e Faça Upload do Código**
   Na Arduino IDE, selecione:
   - Placa: **ESP32 Dev Module**
   - Porta COM correspondente ao ESP32

   Em seguida, clique em **Upload**.

---

## Arquitetura do Sistema

### Componentes
- **ESP32**:
  - Captura dados de corrente, tensão e potência.
  - Processa os dados localmente e os envia para a plataforma **Thinger.io** via Wi-Fi usando o protocolo **MQTT**.
- **Thinger.io**:
  - Funciona como gateway para coleta e gerenciamento dos dados.
  - Exibe os dados coletados em tempo real e permite criar alertas e relatórios para análise do consumo energético.

---

## Funcionalidades do Código

### Estrutura do Código

- **Configuração Inicial**:
  - Conexão ao Wi-Fi.
  - Registro do dispositivo na plataforma **Thinger.io**.
- **Leitura dos Sensores**:
  - Simulação de valores de corrente e tensão.
  - Cálculo da potência com base nos dados simulados.
- **Comunicação com Thinger.io**:
  - Envio dos dados em tempo real para o servidor via **MQTT**.

### Funções Importantes

#### `void connectWiFi()`
Estabelece conexão com a rede Wi-Fi. Em caso de falha, o ESP32 será reiniciado automaticamente.

#### `void lerSensores()`
Lê valores de tensão e corrente simulados e calcula a potência com base na fórmula:
```cpp
potencia = tensao * corrente;
```

#### `void setup()`
Inicializa o dispositivo, conecta ao Wi-Fi e configura os recursos no **Thinger.io**.

#### `void loop()`
Executa as leituras dos sensores, mantém a comunicação com o **Thinger.io** e insere um atraso de 10 segundos antes de repetir.

---

## Expansão do Projeto

- **Monitoramento Avançado**:
  - Integração com dispositivos IoT adicionais.
  - Suporte a fontes de energia renovável.
- **Sustentabilidade**:
  - Relatórios sobre economia de energia e redução de pegada de carbono.
- **Integração com Apps**:
  - Desenvolvimento de um app para monitorar e controlar o consumo em dispositivos móveis.

---
