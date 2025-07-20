# Simulação de Enchimento Automático de Caixas com Silo

Este projeto simula o controle de um **silo automatizado** que enche caixas com auxílio de sensores, válvula solenoide, motor de esteira e indicadores visuais.

## Descrição do Funcionamento

- O sistema enche caixas que são movidas automaticamente por uma **esteira** até ficarem posicionadas sob a **abertura do silo**.
- A abertura do silo é controlada por uma **válvula solenoide**, que libera o conteúdo para a caixa.
- O processo utiliza os seguintes sensores:
  - **Sensor de Presença**: detecta quando uma caixa está posicionada na estação de enchimento.
  - **Sensor de Nível**: detecta quando a caixa atinge o nível máximo de enchimento.

- Três **LEDs indicadores** informam o estado atual do processo:
  - 🟢 LED **RUN**: indica que o sistema está em **funcionamento**.
  - 🔵 LED **FILL**: indica que a caixa está **sendo enchida no momento**.
  - 🔴 LED **FULL**: indica que a caixa **está cheia** (permanece aceso por um curto tempo após o enchimento).

### Enchimento Contínuo

- O sistema enche **várias caixas de forma automática**.
- Após o enchimento de uma caixa:
  - A **esteira é ativada** para mover a caixa cheia para fora.
  - O motor da esteira **para automaticamente** assim que a próxima caixa estiver posicionada corretamente sob o silo (detecção pelo **sensor de presença**).

## Comandos

- **Botão Start**: inicia o processo automatizado de enchimento de caixas.
- **Botão Stop**: interrompe imediatamente qualquer operação em andamento.

## Lógica de Controle

- A automação é baseada na leitura de sensores e no controle sequencial da esteira, válvula e LEDs.
- O sistema só inicia o enchimento se:
  - A **caixa estiver posicionada** corretamente (sensor de presença ativado).
  - A caixa **ainda não estiver cheia** (sensor de nível desativado).
- O LED **FULL** permanece aceso por um pequeno período após o fim do enchimento, como indicação visual de status.

## Observações Importantes

- ⚠️ Durante os meus testes, foi identificado um **vazamento de conteúdo do silo** quando a máquina é iniciada com a **caixa posicionada sobre o sensor de presença, mas ainda fora do sensor de nível**.
- Isso ocorre porque, ao iniciar o sistema, a lógica entende que a caixa está totalmente posicionada e pronta para encher, acionando a válvula solenoide.
- 💡 **Solução sugerida**: Realinhar fisicamente os sensores no projeto da máquina para garantir que **ambos** os sensores (presença e nível) detectem corretamente quando a caixa estiver **realmente posicionada sob o silo**.

## Objetivo

Este projeto tem como finalidade demonstrar o controle automatizado de um sistema de enchimento com:

- Detecção de presença e nível para controle preciso
- Abertura automática da válvula solenoide
- Indicação visual clara do estado atual do processo
- Controle automático da esteira transportadora
- Capacidade de operar de forma contínua com múltiplas caixas
- Parada de emergência via botão **Stop**
