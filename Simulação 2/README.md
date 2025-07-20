# Simulação de Abertura e Fechamento de Portão

Este projeto simula o controle de um **portão com abertura vertical**. O sistema utiliza sensores de posição, LEDs indicadores de estado e comandos manuais, com lógica adicional para segurança e automação.

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

### Fechamento Automático

- Caso o sistema detecte que o portão está totalmente **aberto** por **mais de 8 segundos**, ele aciona automaticamente o **fechamento do portão**.

## Comandos

- **Botão Subir Portão**: envia o comando para iniciar a **subida** do portão.
- **Botão Descer Portão**: envia o comando para iniciar a **descida** do portão.
- **Botão Stop**: **interrompe imediatamente** qualquer movimento do portão.

## Intertravamento de Comandos

> ⚠️ **IMPORTANTE:** Nesta versão, o intertravamento foi alterado de **entrada** para **saída**.

### Como funciona o novo intertravamento por **saída**:

- O comando atual **não pode ser interrompido** por outro comando.
- Se o portão estiver **subindo** e o botão **descer** for pressionado, o comando será **ignorado** até que a subida termine.
- O mesmo ocorre se o portão estiver **descendo** e o botão **subir** for pressionado.
- Isso garante que **não haja conflito entre comandos** e que o movimento iniciado siga até seu fim, salvo se interrompido manualmente.

## Objetivo

Este projeto tem como finalidade demonstrar o controle de um portão automatizado com:

- Monitoramento de estados via sensores
- Indicação visual clara do estado atual
- Lógica de **fechamento automático** após 8 segundos aberto
- **Novo sistema de intertravamento por saída**, evitando mudanças abruptas de direção
- Parada de emergência via botão **Stop**
