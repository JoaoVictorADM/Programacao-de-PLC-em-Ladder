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
  - A capacidade total do tanque é de **306 pulsos**.
  - Cada bomba adiciona **153 pulsos** (50% do total).
  - Há também um contador para o **esvaziamento**, que mede a saída em pulsos.

### LEDs Indicadores

- 🟢 **RUN**: indica que o processo está em execução.
- 🟡 **ENCHENDO** (IDLE na imagem): indica que o tanque está sendo preenchido.
- 🔴 **FULL**: indica que o tanque está completamente cheio.

### Comandos

- **Botão Start**: inicia o processo completo.
- **Botão Stop**: para o processo (algumas etapas não são interrompidas).
- **Botão Reset**: reinicia todos os **contadores de pulsos**.

## Lógica do Processo

1. Ao pressionar **Start**, as bombas 1 e 2 começam a encher o tanque (153 pulsos cada).
2. Quando o tanque está cheio:
   - O **mixer** é ativado por **6 segundos**.
   - Em seguida, o **aquecedor** é ligado até que o sensor acuse **30°C**.
   - Por fim, a **bomba de esvaziamento** é ativada até o tanque ficar **vazio** (baseado em pulsos e sensor de nível).

## Observações Técnicas

- O botão **Stop** não interrompe todas as etapas do processo. Algumas continuam em execução.
- Atualmente, não são utilizadas **variáveis virtuais**, que permitiriam:
  - **Memorizar a etapa atual do processo**.
  - Retomar a operação corretamente após uma parada de emergência.
- Exemplo prático:
  - Se o processo for interrompido durante o **esvaziamento**, e o líquido for retirado manualmente:
    - Ao retomar, o **contador** ainda indicará que o líquido não foi totalmente removido.
    - Sem verificação do **nível real**, o sistema pode tentar acionar a bomba sem necessidade.
- Solução sugerida:
  - Implementar **variáveis de etapa** para controle de sequência.
  - Verificar os sensores antes de retomar qualquer etapa pendente.

## Observações Técnicas

- ⚠️ Algumas etapas do processo **não são paradas com o botão Stop**.
- Atualmente sei da existência de **variáveis "virtuais"**, e sei que conseguiria resolver muita coisa com elas, mas ainda não aprendi a usá-las.
- Uma ideia seria usá-las para simbolizar a **etapa atual do processo**, permitindo que o sistema "lembre" em que ponto estava antes de uma parada.
- Exemplo: no caso do **esvaziamento**, se o processo for interrompido, ao retomá-lo, o sistema poderia continuar a esvaziar de onde parou.
  - Claro, isso exige **verificação do nível do líquido**, pois pode acontecer do processo ser parado e o líquido retirado manualmente.
  - Nesse caso, se **o sensor de nível não for verificado**, o contador continuará achando que há líquido a ser retirado, acionando a bomba desnecessariamente.
- 💡 Solução futura: implementar **variáveis internas (flags de etapa)** junto a verificações de sensores para tornar o processo mais robusto e seguro.

## Objetivo

Este projeto tem como finalidade demonstrar o controle completo de um processo industrial com:

- Enchimento automático controlado por pulsos
- Mistura temporizada do conteúdo
- Aquecimento baseado em leitura de temperatura
- Esvaziamento baseado em pulso e sensor de nível
- Indicação clara de estados com LEDs
- Lógica sequencial com possibilidade futura de implementação de memória de processo
