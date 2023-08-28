# Relatório: Projeto Guess The Number:

O diagrama de circuitos contido no presente repositório refere-se a um projeto proposto pelo professor Ramon Santos Nepomuceno como parte da avaliação da disciplina de circuitos digitais da universidade federal do Cariri, turma 02 de 2023. 

O projeto em questão consiste em um jogo local interativo de dois jogadores, simulado por um circuito combinacional composto por portas, funções e variáveis lógicas, que enfatiza as habilidades de adivinhação individuais de ambos. Seu desenvolvimento se deu sobre intuito de pôr em prática conceitos e métodos voltados à análise, síntese e construção de funções lógicas aplicada a circuitos digitais.

# Visão geral do jogo:

O jogo Guess the Number consiste em um jogo de adivinhação onde dois jogadores competem na tentativa de descobrir um número pré-fixado gerado por sequências de 4 bits. Cada jogador efetua seu palpite em rodadas alternadas das quais o jogo fornecerá informações a respeito do palpite fornecido de modo a orientá-los na escolha do número correto (palpite maior, menor ou igual), vence aquele que primeiro descobrir o número fixado, ou seja, efetuar o palpite de número igual ao valor fixado e o circuito retorna como ligado a saída “número igual”.

# Circuito MAIN:

O circuito main do projeto é composto por dez entradas, sendo oito, quatro para cada jogador, voltadas a composição em binário dos números sugeridos como palpites do primeiro e segundo jogador, uma que funciona como botão para “alternar” as rodadas entre os jogadores (jogador 0 e 1), e uma que funciona como botão “ligar/desligar” do jogo ativando-o quando selecionado. 

Quanto às saídas contidas, o circuito main possui cinco, sendo três responsáveis por orientar os jogadores quanto a adivinhação do valor prefixado, são elas número igual, número maior e número menor, que assinalam a condição do palpite sugerido quando ativadas (1), e duas em formato de display que exibe o palpite repassados pelos jogadores.

O circuito main conta ainda com dois componentes internos responsáveis pelas funcionalidades do game, são eles o conversor_para_o_display e o comb_multicompara, o primeiro presente para cada jogador, recebe como entrada dígitos de valores binários e possui como saídas os valores lógicos, originados de suas operações internas, responsáveis por acender os segmentos de um display encarregado de exibir o valor numérico decimal correspondente a entrada binária fornecida. O segundo por sua vez, dá origem às saídas principais do circuito e recebe diretamente como entrada os valores binários escolhidos pelos jogadores, sendo responsável pela análise comparativa entre estes e o valor pré-fixado alvo da adivinhação, ativando a saída correspondente à condição mais adequada a entrada em relação a este último.

![visão geral do circuito main](https://drive.google.com/file/d/1IXkL6osWscDf0i36JCSQ9YARaWUuO7LT/view?usp=drive_link)
