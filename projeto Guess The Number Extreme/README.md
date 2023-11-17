# Relatório: projeto guess the number extreme

O projeto Guess the number extreme é um jogo em que dois jogadores competem para adivinhar um ponto no espaço, representado por coordenadas x e y, cada uma sendo um número de 4 bits escolhido aleatoriamente. Cada jogador terá a oportunidade de fazer um palpite por vez, indicando uma combinação de coordenadas.

O jogo fornecerá informações sobre a relação entre a soma das coordenadas chutadas e a soma das coordenadas reais do ponto oculto. Ele indicará se a soma das coordenadas é maior, menor ou igual à soma das coordenadas do ponto oculto. Além disso, o jogo informará se o jogador acertou exatamente as coordenadas. Em caso de acerto, um ponto será adicionado ao placar do jogador correspondente e um novo ponto oculto será gerado.

Cada jogador terá um cronômetro associado, que começará a decrementar assim que for a sua vez de fazer um palpite. Ganha o jogador que acertar 15 coordenadas primeiro ou, caso nenhum jogador tenha atingido esse objetivo, aquele que tiver acumulado mais pontos quando ambos os tempos dos jogadores se esgotarem.

# Circuito main: 

O circuito main, referente a interface do jogo propriamente dita pode se analisado como três seções distintas, a primeira relacionada a lógica de controle das rodadas e chutes efetuados por ambos os jogadores, a segunda relacionada a configuração do cronômetro e a correlação de suas métricas com as demais funcionalidades do circuito/jogo, e a terceira relativa a correlação do circuito core com as métricas/leds de andamento do jogo e progresso dos jogadores.

A primeira parte é primordialmente composta por 4 bits conectados a um distribuidor de 4 entradas que direciona seu sinal simultaneamente a um display hexadecimal e um multiplexador enquanto entrada 1, estando a entrada 0 vazia, cujo seletor recebe sinal de uma saída do circuito cronômetro responsável por sinalizar quando todos os dígitos do cronômetro estiverem zerados, isso nos permite que o jogador se encontre impossibilitado de chutar coordenadas caso o tempo do seu cronômetro se esgote. Por continuidade a saída do multiplexador é direcionada a um circuito negador que converte o número, seja ele positivo ou negativo, ao seu equivalente oposto (se positivo passa a negativo e vice-versa), seu sinal, por sua vez é apenas repassado quando verificado que o dígito A3 é 1, caso contrário o sinal original conectado a entrada 0 do mux é direcionado normalmente ao restante do circuito, a mesma lógica repete-se do lado do jogador B com as devidas modificações a fim de garantir o correto funcionamento do mesmo, nesse sentido antes de chegar aos displays hexadecimais responsáveis pela exibição do chute X e Y efetuados, o sinal dos quatro dígitos passa por um subcircuito denominado número escolhido, que
recebe tanto o sinal de 4 bits de A e B, assim como o estado de X referente ao jogador em questão.

Internamente o subcircuito número escolhido é composto por um multiplexador que recebe o número escolhido de A como entrada 0 e o número escolhido de B como entrada 1, além é claro de um seletor que recebe o sinal do estado X, repassando A quando x for 0, e B quando X for 1, esse sinal por sua vez é direcionado a um distribuidor que direciona cada um dos quatro bit a um flip flop d, e tem sua saídas Q conectadas a um distribuidor que direciona os bits armazenados conforme a ativação do clock e do enable ativado pela entrada próximo, a uma saída de 4 bits, isso permite que possamos direcionar o número escolhido correto correspondente ao jogador referente a rodada atual.

![subcircuito número escolhido](https://github.com/Marcondes-Amarante/circuitos-digitais/assets/117780345/45128dd0-ca0b-4b72-8c4b-386c33d8178c)

Voltando ao circuito main a saída do subcircuito número escolhido é encaminhada a outro subcircuito chamado ativador de sinal cuja saída aciona um led caso verificado que o número escolhido original ao passar por um negador da origem a um número complementado cujo bit A3 é igual a 1, e o sinal do jogador A ou jogador B é 1, sendo esse sinal originado por dois flip flops D do main, o primeiro referente ao jogador A que tem como clock o sinal do botão chutar e como excitação o sinal originado por um AND entre o estado X negado do jogador e o sinal do bit A3, armazenado 1 caso x seja 0 e o bit A3 seja 1, da mesma forma para B o equivalente ocorre se ambos forem 1.


