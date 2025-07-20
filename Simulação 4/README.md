

### Ciclo de Funcionamento

1. **Via 1 - Verde** | **Via 2 - Vermelho**
2. **Via 1 - Amarelo** | **Via 2 - Vermelho**
3. **Via 1 - Vermelho** | **Via 2 - Verde**
4. **Via 1 - Vermelho** | **Via 2 - Amarelo**

E o ciclo se repete continuamente, garantindo a fluidez do tráfego.


Simulação de Controle de Tráfego com Semáforos
Este projeto simula o gerenciamento de tráfego em um cruzamento utilizando dois semáforos, controlando o fluxo de veículos de forma alternada entre duas vias.

Descrição do Funcionamento
A simulação representa um cruzamento com duas vias, cada uma com seu respectivo semáforo.
Os semáforos controlam o tráfego de veículos de forma alternada, garantindo a passagem segura em apenas uma direção por vez.
Cada semáforo possui os três LEDs padrão:
🔴 Vermelho
🟡 Amarelo
🟢 Verde
Lógica de Controle
A alternância entre os estados dos semáforos é feita com base em um temporizador cíclico.
O controle dos LEDs de cada semáforo é feito por meio de 6 instruções LIM (Limites), que verificam o valor do temporizador para determinar qual luz deve estar acesa em cada momento do ciclo.
Ciclo de Funcionamento (Exemplo)
Via 1 - Verde | Via 2 - Vermelho
Via 1 - Amarelo | Via 2 - Vermelho
Via 1 - Vermelho | Via 2 - Verde
Via 1 - Vermelho | Via 2 - Amarelo
E o ciclo se repete continuamente, garantindo a fluidez do tráfego.

Estratégia de Implementação
Utilização de:
Temporizador: define o tempo de um ciclo, o valor acumulado é usado para calcular os intervalos.
6 instruções LIM: definem intervalos de tempo dentro dos quais cada cor dos LEDs será ativada para os dois semáforos.
Os LEDs acendem conforme o temporizador atinge determinados valores definidos nas instruções de limite inferior e superior (LIM).
Observações
A simulação mostra o funcionamento sincronizado entre os semáforos de forma contínua.
O temporizador reinicia automaticamente após um ciclo completo, mantendo o controle indefinidamente.
Objetivo
Este projeto tem como finalidade demonstrar:

O controle de tráfego por semáforos automatizados.
A lógica sequencial baseada em temporizador e instruções de faixa (LIM).
O funcionamento seguro e coordenado de dois semáforos em cruzamento.