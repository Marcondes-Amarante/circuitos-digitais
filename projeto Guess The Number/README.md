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

O componente comparador de magnitude, que recebe duas entradas binárias de 4 bits e gera três saídas distintas (igual, maior e menor), é incubido de determinar relações de magnitude comparativa entre as entradas fornecidas enquanto palpites dos jogadores para com o número da constante pré fixado como alvo da adivinhação.

A estruturação do circuito comparador de magnitude é dividida em concordância aos seus tipos de saída possíveis. Para a saída referente a condição A=B, considerando que ambas as entradas são compostas por 4 bits, queremos simular a implicação de igualdade entre o valor de duas entradas, mas especificamente entre seus dígitos internos, logo temos a implementação simulada da função lógica XNOR entre as duas entradas através das portas lógicas básicas AND, OR e NOT, expressas na forma de oito portas AND intercaladas, quatro entre os respectivos dígitos negados de A e B (A0’B0’...A3’B3’), e outras quatro para os respectivos dígitos de A e B (A0B0…A3B3), quatro operações OR, que recebem como entrada as saídas das operações AND (A0’B0’+A0B0…), e por fim uma porta AND que recebe como entradas as saídas das operações OR entre cada um dos dígitos das respectivas entradas (expressas como XOX1X2X3), cuja saída resultante quando em valor lógico alto indica a condição de igualdade entre as entradas.

![circuito comparador de magnitude (A=B)](https://github.com/Marcondes-Amarante/circuitos-digitais/assets/117780345/a1098ed8-6033-4a1c-97ab-cebcb1d43ae9)

Para a saída referente a condição “A maior que B”, a estrutura lógica do circuito se dará sobre a linha de raciocínio comparativa entre os índices de ambas as entradas partindo da esquerda para a direita, ou seja, sobre o sentido A3B3,…,A0B0, onde um dígito da entrada A será maior que um dígito de B se verificado que o dígito de A analisado possui valor lógico alto comparado a B (ex: A0 = 1 e B0= 0), de tal maneira concebe-se 4 possibilidades da entrada A ser maior que B são elas: 

- A3 > B3 (A3=1, B3=0)
- A3=B3 e A2>B2 (A2=1, B2=0)
- A3=B3 e A2=B2 e A1>B1 (A1=1, B1=0)
- A3=B3 A2=B2 A1=B1 e A0>B0. (A0=1, B0=0)

Essas expressões booleanas comparativas foram representadas em um circuito combinacional através de 4 portas lógicas AND que receberam como entrada os dois dígitos a serem comparados, estando o segundo negado, além é claro dos resultados das comparações de igualdades entre os dígitos que os antecedem para os casos a partir de A3=B3 A2>B2, comparações estas que nada mais são que as saídas das portas OR relativas a seção anterior do circuito responsável pela verificação da condição de igualdade, todas as saídas dessas 4 portas AND descritas são direcionadas para uma porta OR cuja saída será assinalada como nível lógico alto caso verificado a veracidade de uma das 4 condições acima.

![circuito comparador de magnitude (A maior que B)](https://github.com/Marcondes-Amarante/circuitos-digitais/assets/117780345/dd205977-8907-419c-b12d-cbd3c2c30409)

Por fim, para a saída referente a condição “A menor que B” a estrutura lógica comparativa empregada ao circuito se dará de forma analogamente semelhante a seção anterior do circuito, os índices constituintes de ambas as entradas continuarão a serem analisados da esquerda para a direita, mas desta vez um dígito da entrada A será menor que um dígito da entrada B quando verificado valor lógico baixo (0) do dígito A e valor lógico alto (1) referente ao dígito B, dessa forma concebemos 4 possibilidades dos dígitos da entrada A serem menores que os dígitos de B, são elas:

- A3<B3 (A3=0, B3=1)
- A3=B3 A2<B2 (A2=0, B2=1)
- A3=B3 A2=B2 A1<B1 (A1=0, B1=1)
- A3=B3 A2=B2 A1=B1 A0<B0 (A0=0, B0=1)

Essas expressões booleanas comparativas foram representadas em um circuito combinacional utilizando, assim como a seção anterior, 4 portas AND, que recebem como entradas dois dígitos a serem comparados constituintes das entradas A e B, estando o primeiro negado, além é claro das comparações de igualdade previamente efetuadas em relação às portas AND cuja entradas analisadas possuem dígitos precedentes de valor lógico iguais (como no caso 2 em diante). Todas as saídas dessas 4 portas AND foram direcionadas a uma porta OR cuja saída é sinalizada por nível lógico alto se umas das portas descritas for verificada como verdadeira (1).

![circuito comparador de magnitude (A menor que B)](https://github.com/Marcondes-Amarante/circuitos-digitais/assets/117780345/20ebf290-d342-44ca-b5d8-26741d2cb24a)
