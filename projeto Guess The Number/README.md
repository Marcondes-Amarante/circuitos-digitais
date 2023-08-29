# Relatório: Projeto Guess The Number:

O diagrama de circuitos contido no presente repositório refere-se a um projeto proposto pelo professor Ramon Santos Nepomuceno como parte da avaliação da disciplina de circuitos digitais da universidade federal do Cariri, turma 02 de 2023. 

O projeto em questão consiste em um jogo local interativo de dois jogadores, simulado por um circuito combinacional composto por portas, funções e variáveis lógicas, que enfatiza as habilidades de adivinhação individuais de ambos. Seu desenvolvimento se deu sobre intuito de pôr em prática conceitos e métodos voltados à análise, síntese e construção de funções lógicas aplicada a circuitos digitais.

# Visão geral do jogo:

O jogo Guess the Number consiste em um jogo de adivinhação onde dois jogadores competem na tentativa de descobrir um número pré-fixado gerado por sequências de 4 bits. Cada jogador efetua seu palpite em rodadas alternadas das quais o jogo fornecerá informações a respeito do palpite fornecido de modo a orientá-los na escolha do número correto (palpite maior, menor ou igual), vence aquele que primeiro descobrir o número fixado, ou seja, efetuar o palpite de número igual ao valor fixado e o circuito retorna como ligado a saída “número igual”.

# Circuito MAIN:

O circuito main do projeto é composto por dez entradas, sendo oito, quatro para cada jogador, voltadas a composição em binário dos números sugeridos como palpites do primeiro e segundo jogador, uma que funciona como botão para “alternar” as rodadas entre os jogadores (jogador 0 e 1), e uma que funciona como botão “ligar/desligar” do jogo ativando-o quando selecionado. 

Quanto às saídas contidas, o circuito main possui cinco, sendo três responsáveis por orientar os jogadores quanto a adivinhação do valor prefixado, são elas número igual, número maior e número menor, que assinalam a condição do palpite sugerido quando ativadas (1), e duas em formato de display que exibe o palpite repassados pelos jogadores.

O circuito main conta ainda com dois componentes internos responsáveis pelas funcionalidades do game, são eles o conversor_para_o_display e o comb_multicompara, o primeiro presente para cada jogador, recebe como entrada dígitos de valores binários e possui como saídas os valores lógicos, originados de suas operações internas, responsáveis por acender os segmentos de um display encarregado de exibir o valor numérico decimal correspondente a entrada binária fornecida. O segundo por sua vez, dá origem às saídas principais do circuito e recebe diretamente como entrada os valores binários escolhidos pelos jogadores, sendo responsável pela análise comparativa entre estes e o valor pré-fixado alvo da adivinhação, ativando a saída correspondente à condição mais adequada a entrada em relação a este último.

![visão geral do circuito Main](https://github.com/Marcondes-Amarante/circuitos-digitais/assets/117780345/ce90b9a5-a3a9-4987-8c54-d81ec997c15a)

# Comb_MultiCompara:

O componente Comb_MultiCompara em conjunto aos seus componentes internos possui a função de mediar e gerir as operações comparativas entre os palpites fornecidos para com a constante fixada, e possui em sua composição quatro entradas, sendo duas entradas de 4 bits, uma entrada responsável por acionar a jogada e outra que funciona como seletor/identificador dos jogadores. Como saída o circuito em questão possui as condicionais representadas como status comparativo entre o palpite e número fixado que é representado internamente como uma constante. 

Em relação aos seus componentes constituintes, o Comb_Multicompara possui um circuito multiplexador associado às duas entradas de 4 bits, o seletor/identificador do jogador, o botão de acionar o jogo,  e um circuito comparador_de_magnitude, que recebe como entrada a constante fixada e a saída do multiplexador, sendo associado a três portas AND, que recebem suas saídas e o botão jogar, retornando os respectivos valores lógicos de “status” do circuito combinação multi compara.

![visão geral do circuito Comb_MultiCompara](https://github.com/Marcondes-Amarante/circuitos-digitais/assets/117780345/37d81968-2dbb-4efa-84ec-2a87e8f4aa63)

# Multiplexador:

O circuito multiplexador, tipicamente encarregado de selecionar uma entre várias entradas e direcioná-la para uma única saída, foi implementado em nosso sistema sobre a configuração 2 para 1. 

Funcionando como um seletor, direcionado por uma entrada de seleção com largura de 4 bits de dados, o multiplexador implementado é composto por duas entradas A e B de 4 bits que referem-se aos valores binários fornecidos pelos jogadores, duas portas AND, e uma porta OR, também com larguras de 4 bits, cuja saída resultante é concebida como uma das entradas definidas pelo valor lógico relativo ao bit seletor. 

O destaque aqui vai para a implementação do seletor em associação a uma conexão distribuidora que permite a extensão do sinal do seletor sobre uma largura de 4 bits, possibilitando a compatibilidade de larguras entre as entradas e portas lógicas delimitadas, sendo assim, quando o seletor for 0 inferimos 0000 e direcionamos para a saída o valor da entrada A, e quando 1 infere-se o seletor como 1111 e direcionamos para a saída o valor da entrada B.

![circuito multiplexador](https://github.com/Marcondes-Amarante/circuitos-digitais/assets/117780345/84dc6673-c11a-4597-8a89-c5b8ae8ca524)

# Comparador de magnitude:

o comparador de magnitude
