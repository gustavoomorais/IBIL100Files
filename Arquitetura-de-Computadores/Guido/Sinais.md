# Arquitetura de Computadores

----
### Sumário

#### Por Matéria

- Sinais
  - [Noções de Sinais e Processamento por Computadores](#nocoes)
  - [Questões relativas a propagação das ondas](#questoes)


#### Por Aula

- [Aula 1 - 20/03/2015](#aula1)
- [Aula 2 - 27/03/2015](#aula2)
- [Aula 3 - 10/04/2015](#aula3)
- [Aula 4](#aula4)

----
----
###<a name="aula1"></a> Aula 1 - 20/03/2015
----

###<a name="nocoes"></a> Noções de Sinais e Processamento por Computadores 

Sinal é uma entidade física que descreve matematicamente a emissão de algum tipo de energia e como ela varia ao longo do tempo.
> **Ex:** Sinal de áudio, sinal de voz, sinal de rádio, entre outros.

Os sinais estão divididos basicamente em dois grupos:
- Unidimensionais (1D)
- Bidimensionais (2D)

No primeiro caso existe uma variação de energia em função de uma variável, que normalmente é o tempo. No segundo caso, por outro lado, a quantidade de energia é função de 2 variáveis, tais como coordenada horizontal e coordenada vertical. Na prática, sinais 1D contemplam áudio, voz, emissão de rádio, emissões biomédicas e neuronais, entre outros. Já sinais 2D correspondem imagens.

Importante também é definir o termo **processamento**, que constitui qualquer tipo de manipulação, análise, modificação e até mesmo síntese, isto é, fabricação de algo. Desse modo, o processamento de sinal consiste em analisá-lo, modifica-lo, etc.

Existe basicamente duas formas para realizar processamento de sinais:

- Processamento Analógico
- Processamento Digital


Na primeira modalidade são empregados circuitos eletrônicos que utilizam resistores, capacitores, transistores, indutores, entre outros, **mas não há processador**.

Na segunda modalidade, circuitos eletrônicos também são utilizados, mas **o componente base é o processador**.

Isso faz com que ambas as modalidades possuam características distintas. No primeiro caso, isto é, analógico, todo sinal é processado continuamente, sem perdas. Enquanto no segundo caso, isto é, digital, somente pontos específicos são processados, pois o processador trabalha somente com valores pontuais, e não tem capacidade para processar infinitos valores.

Lembramos ainda que circuitos eletrônicos analógicos, são construídos com finalidade específica, como por ex. amplificar a voz, robotizar a voz, e assim por diante. Qualquer modificação no propósito do processamento implica na construção de um novo circuito eletrônico, demandando tempo e custo. Por outro lado, a modificação de propósito no processamento digital implica simplesmente em alterar o software correspondente. 

#### Em suma, temos a seguinte situação:
**Processamento Analógico**
- Vantagem: Trabalha com todo o sinal.
- Desvantagem: Mudança de objetivo significa construir um novo circuito.

**Processamento Digital**
- Vantagem: Mudança de propósito = mudança no software
- Desvantagem: Não é possível tratar os infinitos pontos do sinal

Certamente temos uma motivação maior para realizar processamento digital ao invés do analógico. Para isso precisamos definir qual é a quantidade de pontos, isto é, valores, que temos de processar em meio aos infinitos valores existentes em um sinal qualquer. Para isso utilizamos uma teoria de fundamental importância, e que possibilitou o processamento digital de sinais não textuais, que é conhecida como Teorema da Amostragem, ou **Teorema de Nyquist**.

---

###<a name="aula2"></a> Aula 2 - 27/03/2015 

O teorema da amostragem, ou o teorema de Nyquist, é um resultado do qual podemos fazer uso para realizar um processamento digital de sinais, sendo que de acordo com ele, é necessário entregar ao processador, um número de pontos, isto é, amostras, que é pelo menos igual ao dobro da máxima frequência presente no sinal analógico respectivo.

Em se tratando de sinais de áudio, por exemplo, que constituem os sinais multimídia mais elementares, existe outro resultado experimental garantindo que o ouvido humano não é capaz de perceber frequências acima de 22050 Hz. Desse modo, com base em ambos os resultados é possível concluir que a taxa de amostragem de 22050 x 2 = 44100 am/seg é suficiente para manipular de modo digital os sinais de áudio, lembrando ainda que as amostras devem ser igualmente espaçadas. O processo de amostragem, faz com que o sinal originalmente contínuo seja caracterizado como sinal discreto.

A questão da discretização realizada no eixo horizontal também é necessária no eixo vertical. Este procedimento, que é chamado **quantização** implica em dividir o eixo das amplitudes (vertical) em uma quantidade finita de pontos e utilizar apenas um deles para cada amostra capturada. Assim, por exemplo, se temos amplitudes, no modo contínuo, variando de -5 até 5 e optamos por uma quantização de 1 em 1, então o valor da amostra que no mundo real é "2.74512" será armazenado na versão discreta como o número 3, pois é o valor de amplitude mais próximo existente no mundo digital.

A quantização, diferentemente da amostragem que é regulada genericamente para qualquer sinal, não é expressa para sinais quaisquer de um modo único. Ao contrário, cada tipo de sinal possui uma quantização ideal. De qualquer forma dizemos que a quantização é de ‘X’ bits, sendo ‘X’ obtido experimentalmente de acordo com o tipo de sinal. Quantizações tradicionais são, por exemplo, 8 bits para voz, 16 bits para áudio e música em geral, 24 bits para sinais biomédicos, o que equivale respectivamente a 2^8 = 256, 2^16 = 65.536, 2^24 = 16.777.216

Normalmente, a não ser em casos específicos, os valores são os inteiros correspondentes, admitindo-se que um dos bits seja utilizado para representar o sinal positivo ou negativo. Desse modo, utilizando 8 bits temos valores inteiros que estão na faixa `-128 ~ 127`, utilizando 16 bits `-32.768 ~ 32.767`, e utilizando 24 bits `-8.388.608 ~ 8.388.607`.
Assim sendo, um sinal musical armazenado no computador, por exemplo, é na verdade um vetor de 44.100 pontos a cada segundo, para o qual cada posição do vetor é um valor inteiro na faixa de `-32.768 ~ 32.767`.

Quando convertemos o sinal contínuo em sinal discreto, com base no teorema da amostragem, dizemos que o sinal foi **discretizado**. Por outro lado, quando aplicamos os arredondamentos necessários no eixo das amplitudes, dizemos que o sinal foi **quantizado**. Após a aplicação de ambos os processos, dizemos que o sinal, que era originalmente analógico, passou a ser **digital**.

>**Demonstração**: Existe um fenômeno natural que, embora não constitua uma demonstração teórica é suficiente para exemplificar na prática o teorema da amostragem, trata-se do fenômeno que nos dá a falsa impressão de que as rodas de um veículo em movimento estão girando em sentido contrário ao do veículo. Tendo em vista que o olho humano não é um sistema contínuo de detecção de movimento, assume-se uma situação na qual ocorre amostragem, isto é, somos somente capazes de ver e de codificar um número finito de quadros ao longo do tempo, normalmente cerca de 15 ou 20 imagens por segundo. Assim sendo, quando as rodas do veículo giram em uma taxa baixa as amostras capturadas pelo olho na sequência bastam para perceber o movimento no sentido correto. Por outro lado, quando a velocidade é tal que entre cada amostra as rodas giram mais do que meia volta passamos a ter a percepção errada, que volta a ficar correta caso, entre cada amostra elas girem pouco mais de uma volta e assim por diante. Notamos ainda o caso no qual a taxa de amostragem no olho coincide com exatamente ‘N’ voltas da roda, sendo N = 1,2, 3, ..., ∞; que implica em perceber erroneamente a roda parada. A solução que conduz a percepção correta requer que entre cada ciclo seja possível amostrar pelo menos mais uma vez, o que implica que a taxa de amostragem, para percepção correta, deve ser pelo menos o dobro do número de ciclos, isto é, da máxima frequência.

A percepção errônea corresponde a uma frequência fantasma que, formalmente recebe o nome de **Aliasing**. É muito importante notar que o circuito eletrônico responsável por amostrar e quantizar sinais do meio externo deve ter uma precisão extrema. Isso significa que no momento exato de capturar cada amostra o circuito não pode falhar, ou demorar, pois caso contrário outro valor de amplitude será capturado, confundindo o momento ideal com outro produzindo a distorção do sinal, possível aliasing entre outros efeitos danosos que inviabilizam por completo o processamento digital do sinal. Desse modo, é necessário que exista um dispositivo, que normalmente é um **processador dedicado**, para realizar a amostragem. Este processador está, no caso de um sinal de áudio por exemplo, na placa de áudio. No caso de uma câmera digital este dispositivo está na respectiva placa de captura de imagens, e assim por diante. De qualquer forma não devemos tentar utilizar o processador principal da máquina para controlar a amostragem, pois certamente o sistema operacional suspenderia o processo que cuida da amostragem para atender, de tempos em tempos, outros processos, tais como os que cuidam da rede, de entrada e saída no teclado e mouse, entre outros.

Notamos que independentemente do processador que controla a amostragem, ele só pode trabalhar com os dados já digitalizados, e portanto a amostragem e a quantização necessitam adicionalmente ao processador um circuito eletrônico conhecido como **Conversor Analógico-Digital (AD)**. No caso de desejarmos algum processamento ou modificação dos dados digitalizados, o respectivo software será executado no processador principal da máquina de modo que a comunicação entre os componentes eletrônicos envolvidos é dada por um conjuntos de vias de comunicação elétrica chamada de **barramento**, conforme estudaremos a diante.

#### MINI PROVA 1 (PRÓXIMA AULA) 
- ELABORAR UM TEXTO COM 2/3 PARÁGRAFOS CURTOS DISCUTINDO AS IMPLICAÇÕES, AS VANTAGENS E AS DESVANTAGENS DE REALIZAR PROCESSAMENTO DIGITAL DE SINAIS FRENTE A ABORDAGEM ANALÓGICA. 

----

###<a name="aula3"></a> Aula 3 - 10/04/2015

----

###<a name="questoes"></a> Questões relativas a propagação das ondas 


#### Fundamentos de comunicação de dados

Em arquitetura de computadores estudaremos as interligações e as diversas disposições dos componentes eletrônicos que formam um computador. Esses componentes estão interligados e portanto se comunicam por meio de sinais elétricos, mesmo que a distância entre eles seja mínima. Esta comunicação é também alvo do nosso estudo pois normalmente impõe barreiras no que se refere a distância e aos locais de conexão dos componentes diversos. Os mesmos conceitos aqui discutidos servem de base para o entendimento da comunicação entre computadores e outros aparelhos. 
Inicialmente é importante lembrar que qualquer condutor de eletricidade, tal como cobre, a prata, o ouro, entre outros, possui o seu comportamento modelado em função de 3 elementos, isto é, 3 grandezas físicas:

- Resistência: `R`
- Capacitância: `C`
- Indutância: `L`

A resistência, também chamada de resistência ôhmica interfere de modo a fazer uma força contrária a da passagem da corrente elétrica, independentemente do sinal que atravessa o condutor, ser contínuo, alternado, com alta ou baixa amplitude, entre outros fatores. Desse modo, a atenuação causada pela resistência ôhmica é a mesma para qualquer situação, fazendo com que ela seja uma característica não reativa. Usualmente representamos a resistência ôhmica com o símbolo `R`.

Com relação a capacitância, normalmente simbolizada com a letra `C`, temos um efeito distinto da resistência. Em corrente contínua um capacitor, que é o componente eletrônico responsável por prover capacitância, permite a passagem de corrente elétrica até que ele atinja a sua carga completa que é função do seu valor dado em farads.

O indultor, por outro lado, apresenta um comportamento inverso ao do capacitor. Em um circuito elétrico de corrente contínua, o indultor oferece uma oposição a passagem da corrente quando ela é aplicada, até o ponto em que, após alguns instantes, dependendo do valor do indultor medido em Henrys, ele se satura, permitindo assim o fluxo integral da corrente elétrica.

> **TODO**: Desenho das lâmpadas em cada tipo.

Em vista dos comentários acima, e entendendo qualquer condutor possui as propriedades `R`, `L` e `C` intrínsecas, é fácil entender que quando transmitimos, por meio de um condutor, um sinal elétrico de um ponto ao outro, estamos sujeitos aos 3 elementos físicos retromencionados. Conforme podemos observar na figura abaixo o sinal contínuo transmitido é diferente do sinal recebido, enquanto a situação de `C` e de `L` não atinja estabilidade. Este intervalo de tempo é conhecido como **transiente**.

> **TODO**: Gráfico continuo

Tendo em vista o comportamento do condutor em corrente contínua, conforme o gráfico acima, que é conhecido como gráfico de resposta ao degrau, podemos facilmente compreender o comportamento do condutor em corrente alternada, conforme o gráfico a seguir.

> **TODO**: Gráfico oscilando

Constatamos, pelo exame do gráfico acima, que a corrente alternada transmitida, representada na forma de uma onda retangular, é simplesmente um conjunto de degraus, isto é, transições entre 0 e 5 volts. Assim sendo, o sinal recebido, possui inúmeros períodos transientes em torno de cada degrau. Ocasionando a curva do sinal recebido no gráfico. Concluindo, podemos entender que a rigor, não existe transmissão efetiva de uma onda quadrada, pois ela contém sempre inúmeros transientes que correspondem a um conjunto de oscilações senoidais. O estudo mais aprofundado do tema mostra que uma onda quadrada ou retangular, assim como qualquer outra forma de onda não senoidal, é uma soma de infinitas senóides, cada uma com sua frequência e amplitude específica. Este estudo, tem os seus resultados assegurados por meio das **séries de Fourier**. Importante ainda é compreender que com base nas séries de Fourier, o fato do sinal recebido ser diferente do transmitido, ocorre porque as senóides de frequências mais altas não conseguem alcançar o ponto receptor do sinal devido as propriedades `L` e `C` do condutor. Em geral, cada condutor com seus tamanhos e demais particularidades é equivalente a um conjunto `R`, `L` e `C` que, na prática, não oferece alteração substancial no sinal transmitido desde que cada degrau não tenha um período de duração muito pequeno, isto é, uma frequência muito alta. A frequência limite das senóides que atravessam o condutor sem alteração substancial recebe o nome de **largura de banda**.

Dentre as inúmeras possiblidades de efetuar transmissão de dados entre dois pontos, a opção que utiliza a base 2 é a melhor, pois próximos aos degraus existentes no sinal, as distorções oferecem uma margem pequena de erro, pois assumindo por exemplo que os níveis lógicos 0 e 1 correspondam na realidade física a 0 e a 5 volts respectivamente basta um único limiar em 2,5 volts por exemplo. Níveis de tensão abaixo do limiar são interpretados como lógica 0, e níveis acima do limiar como lógica 1. Se por outro lado tivéssemos 3 ou mais níveis precisaríamos de 2 ou mais limiares respectivamente, aumentando assim a possibilidade de erro interpretação. O caso extremo é o que possui **infinitos níveis**, correspondendo assim ao **sinal analógico**. Além disso, a base 2 oferece possiblidades mais simples para realizar cálculos diversos nos processadores e desse modo é a opção adotada, para qual não existe qualquer previsão ou intenção de alteração.

A possiblidade de uso da base 2 foi se consolidando ao longo das diversas gerações de computadores ao longo dos tempos. Particularmente, todas as máquinas e equipamentos de desenvolvidos com a finalidade de realizar cálculos até o ano de 1945 englobam o que chamamos de **Geração 0** de computadores, na qual incluímos basicamente as réguas de cálculo e as máquinas calculadoras, que atualmente constituem peças de museu. Entre 1945 e 1955, passamos a ter a **Geração 1** de computadores, que eram basicamente constituídos de válvulas eletrônicas. Tais computadores normalmente ocupavam espaços físicos imensos e nos quais a temperatura média chegava aos 50~60 °C. Tal fato, implicava em manter os referidos computadores em gigantescos armários térmicos, sendo ainda necessário realizar trocas de cabeamento e conexões para que o computador fosse reprogramado.

Com os avanços nas pesquisas, alcançamos a **Geração 2** de computadores que vão de 1955 a 1965. Nesta geração a base dos circuitos foi o transistor semicondutor em sua versão discreta. Os transistores constituem componentes eletrônicos com função básica de amplificação e comutação de sinais, sendo constituídos basicamente de 1 dentre 2 minerais naturais: **Silício** e **Germânio**, ambos constantes da tabela periódica. Para o correto funcionamento, os transistores são constituídos de 1 desses minerais especialmente preparados com base num processo químico conhecido como dopagem e que tem a função de acrescentar impurezas aos minerais necessárias ao funcionamento do componente. O processo, que se tornou de baixo custo, requer maquinário considerado como muito específico, tendo sido inicialmente desenvolvido no Bell Labs nos EUA. Uma característica peculiar dos transistores é que eles requerem tensões e correntes baixíssimas para funcionar, entretanto, são fisicamente quase microscópicos. Visando, desse modo, permitir o uso industrial e comercial deles, faz-se necessário encapsulá-los em uma massa plástica que os torna muito maiores. Assim o transistor discreto, como é popularmente chamado, é muito maior que o transistor real.

Com o advento da tecnologia mecânica, a indústria passou a ser capaz de manipular mais facilmente elementos quase microscópicos, dessa forma foi possível passar a conectar vários desses elementos e assim encapsulá-los em um único invólucro. Desse modo, surgiu então entre 1965 e 1980 a **Geração 3** de computadores que era basicamente constituída de conjuntos de transistores encapsulados juntos, fato este que deu origem ao nome **Circuito Integrado**. Após a década de 80, o avanço da tecnologia permitiu a construção de máquinas capazes de agrupar milhões de transistores em um único circuito integrado. Esse fato conduziu a **Geração 4** de computadores, também conhecida como geração de Very Large Scale Integration (VLSI). Os avanços tecnológicos, tanto em nível de fabricação de componente quanto em nível de programação deles via software, fez com que após o ano 2000 uma nova geração, conhecida como **Geração 5** de computadores fosse definida. Nela, encontramos muitos milhões de transistores e outros componentes em um único circuito integrado que conta ainda com reduções drásticas de tamanho físico. Essa geração é também conhecida como das máquinas de baixa potência, ou máquinas "invisíveis" ou até **máquinas descartáveis**. Exemplos são os smartphones, tablets, entre outros, inclusive cartões de Radio Frequency Identification(RFID). 

A atuação conjunta software-hardware, somada ao desenvolvimento técnico-mecânico de fabricação dos circuitos integrados fez com que as máquinas de baixa potência ou descartáveis estivessem disseminadas em toda a indústria eletrônica, passando então a compor os mais diversos aparelhos, tais como, geladeiras, máquinas de lavar, brinquedos, relógios, entre outros. Desenvolveu-se inclusive uma linha de pesquisa para tratar particularmente desse tema de pesquisa que é conhecida como computação **ubíqua** ou **pervasiva**.

#### MINI PROVA 2 (PRÓXIMA AULA)
- ELABORE UM PEQUENO TEXTO RESUMINDO E DISCUTINDO OS CONCEITOS DE CADA UMA DAS 5 GERAÇÕES DE COMPUTADORES.

----

###<a name="aula4"></a> Aula 4
