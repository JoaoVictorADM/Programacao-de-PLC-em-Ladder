# Simulação de Processo de Enchimento, Mistura, Aquecimento e Esvaziamento de Tanque

Este projeto simula o controle completo de um **tanque industrial** que passa pelas etapas de enchimento com dois líquidos, mistura, aquecimento e esvaziamento, utilizando sensores, contadores, atuadores e lógica sequencial.

## Descrição do Funcionamento

O sistema controla as seguintes etapas:

1. **Enchimento**: duas bombas preenchem o tanque, cada uma com um tipo de líquido.
2. **Mistura**: um **mixer** agita o conteúdo do tanque por um tempo determinado.
3. **Aquecimento**: o líquido é aquecido até atingir uma temperatura definida.
4. **Esvaziamento**: uma bomba retira o líquido do tanque.

### Equipamentos e Componentes Utilizados

- **2 Bombas de Enchimento** (Bomba 1 e Bomba 2)
- **1 Bomba de Esvaziamento**
- **1 Mixer** para agitar o conteúdo
- **1 Aquecedor**
- **Sensor de Nível Inferior**: detecta se o tanque está **vazio**
- **Sensor de Nível Superior**: detecta se o tanque está **cheio**
- **Sensor de Temperatura**: identifica se a temperatura atingiu **30°C**
- **Contadores de Pulso**:
  - Cada bomba enche o tanque baseado em pulsos.
  - A capacidade total do tanque é definida com base nos litros configurados.
  - Há também um contador para o **esvaziamento**, que mede a saída em pulsos.
- **Chave Seletora de Ciclos**: para selecionar a quantidade de ciclos do processo.
- **Display BCD (Saída O:4)**: para mostrar o volume atual do tanque em litros.

### LEDs Indicadores

- 🟢 **RUN**: indica que o processo está em execução.
- 🟡 **ENCHENDO**: indica que o tanque está sendo preenchido.
- 🔴 **FULL**: indica que o tanque está completamente cheio.

### Comandos

- **Botão Start**: inicia o processo completo.
- **Botão Stop**: para o processo (algumas etapas não são interrompidas).
- **Botão Enter**: confirma os parâmetros de entrada (litros e número de ciclos).

## Novas Funcionalidades

### Controle de Repetição com Chave Seletora

- Uma **chave seletora** permite definir **quantas vezes o processo completo será repetido**:
  - 🔘 **Posição A**: 1 ciclo
  - 🔘 **Posição B**: 3 ciclos
  - 🔘 **Posição C**: 5 ciclos
- O sistema executa todas as etapas para cada ciclo e **encerra automaticamente** após completar o número programado.

### Definição de Quantidade de Litros

- Um **valor numérico em BCD** é inserido através de um painel ou entrada digital.
- Esse valor representa **quantos litros devem ser colocados no tanque**.
- Ao pressionar o **Botão Enter**, o valor é:
  - Convertido de BCD para inteiro (`FRD`)
  - Armazenado em uma variável de processo
  - **Dividido por 2**, e cada bomba enche **metade** da quantidade definida

### Display Digital

- Um **display conectado à saída BCD** mostra **quantos litros há atualmente no tanque**.
- Esse valor é:
  - Calculado com base nos pulsos de entrada das bombas
  - Atualizado a cada ciclo de enchimento
  - Convertido de inteiro para BCD (`TOD`) antes de ser enviado à saída

## Lógica do Processo

1. O operador define:
   - Quantidade de **litros a serem colocados**
   - Quantidade de **ciclos completos** a serem executados
   - Pressiona o **Botão Enter** para confirmar
2. Ao pressionar **Start**, o processo começa:
   - As bombas enchem metade da quantidade cada
   - O mixer é ativado por **4 segundos**
   - O aquecedor liga até a temperatura atingir **25°C**
   - O líquido é esvaziado por pulsos e sensores
   - O valor atual de litros é mostrado no **display digital**
3. O processo se repete até atingir o número de ciclos definidos.
4. Ao final, o sistema **desliga automaticamente**.

## Objetivo

Este projeto tem como finalidade demonstrar o controle completo de um processo industrial com:

- Enchimento automático baseado em valor configurado em litros
- Distribuição igual entre duas bombas
- Mistura temporizada do conteúdo
- Aquecimento baseado em leitura de temperatura
- Esvaziamento controlado por pulsos e sensores
- Indicação clara de estados com LEDs e display digital
- Repetição do processo baseado em chave seletora de ciclos
- Confirmação de parâmetros com botão ENTER
- Lógica sequencial com possibilidade futura de memória de processo
