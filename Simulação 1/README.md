# Simulação de Abertura e Fechamento de Portão

Este projeto simula o controle de um **portão com abertura vertical**. O sistema utiliza sensores de posição, LEDs indicadores de estado e comandos manuais, com lógica adicional para segurança.

## Descrição do Funcionamento

- O portão pode ser **aberto** ou **fechado** por comandos manuais.
- Dois **sensores de posição** são utilizados:
  - **Sensor Inferior**: detecta quando o portão está totalmente **fechado**.
  - **Sensor Superior**: detecta quando o portão está totalmente **aberto**.
- Se nenhum dos sensores estiver ativo, o portão está em estado **entreaberto**.
- Três **LEDs indicadores** informam o estado atual:
  - 🔴 LED de **Fechado**
  - 🟡 LED de **Entreaberto**
  - 🟢 LED de **Aberto**

## Comandos

- **Botão Subir Portão**: envia o comando para iniciar a **subida** do portão.
- **Botão Descer Portão**: envia o comando para iniciar a **descida** do portão.
- **Botão Stop**: **interrompe imediatamente** qualquer movimento do portão.

## Intertravamento de Comandos

Foi implementado um **intertravamento de entradas** para garantir a segurança e o controle adequado do movimento:

- Se o portão estiver **subindo** e for pressionado o botão de **descer**, ele **inverte o movimento** e começa a descer imediatamente.
- O mesmo ocorre no sentido oposto: se estiver **descendo** e for pressionado o botão de **subir**, o portão muda de direção e sobe.
- O botão **Stop** interrompe qualquer comando em execução, parando o portão no ponto atual.


## Objetivo

Este projeto tem como finalidade demonstrar o controle de um portão automatizado com:

- Monitoramento de estados via sensores
- Indicação visual clara do estado atual
- Resposta rápida a comandos conflitantes
- Parada de emergência via botão **Stop**

