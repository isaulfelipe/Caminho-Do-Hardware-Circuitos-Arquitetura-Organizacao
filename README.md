# O Caminho do Hardware: Circuitos, Arquitetura e Organização.

## 1. Fundamentos de Circuitos Digitais.

### 1.1 Sistemas de Numeração:
   * Decimal: O sistema de numeração que usamos no dia a dia. Estamos acustumados e é intuitivo para gente.
   * HexaDecimal: Sistema de numeração posicional que utiliza 16 símbolos distintos para representar números. Ele usa os 10 dígitos decimais de 0 a 9 mais as 6 primeiras letras do alfabeto: A, B, C, D, E, F.
   * Octal: O sistema octal utiliza apenas 8 símbolos para representar números: os dígitos de 0 a 7. Símbolos: 0,1,2,3,4,5,6,7. Quando a contagem atinge 7, o próximo número é o 10 (equivalente a 8 em decimal), pois a "casa" do 8 não existe e há um "carregamento" para a próxima posição.
   * Binario: O mais simples dos sistemas posicionais. Símbolos: 0,1. Cada um desses símbolos é chamado de bit. É o sistema fundamental da computação, que representa informações usando apenas dois estados: 0 e 1.

### 1.2 Conversão
#### 1.2.1 Conversão Decimal-Binário para Números >= 0 :
![Fonte: WikiHow](https://www.wikihow.com/images/thumb/4/45/Convert-from-Decimal-to-Binary-Step-9-Version-4.jpg/v4-728px-Convert-from-Decimal-to-Binary-Step-9-Version-4.jpg "Fonte WikiHow")

Após isso adicione um 0 a esquerda
#### 1.2.2 Conversão Decimal-Binário para Números <= 0:
   * Pegue o modulo do numero que você quer converter de decimal para binario e faça o topico 1.2.1 normalmente com o modulo desse numero, após isso basta apenas repetir os números até encontrar o primeiro 1 e depois trocar todos os 1 por 0 e 0 por 1.
#### 1.2.3 Conversão Binário-Decimal para Números >= 0:
![Fonte: @isaulfelipe0]( /arq/img/ConversaoBinarioDecimalParaNumerosPositivos.png "Fonte @isaulfelipe")
#### 1.2.4 Conversão Binário-Decimal para Números <= 0:
   * Basta apenas repetir os números até encontrar o primeiro 1 e depois trocar todos os 1 por 0 e 0 por 1, após isso, faça o topico 1.2.3 com o modulo desse número e depois ponha o sinal de negativo(-).

### 1.3 Portas Lógicas
#### 1.3.1 Not:
   * Invente o valor de uma proposição.
#### 1.3.2 And:
   * Só é verdade quando ambas proposiçãoes são verdadeiras
      * Mantra da AND: Zero na entrada, zero na saída.
#### 1.3.3 Nand:
   * É a AND com uma Not no final
      * Só é falso quando todas as proposiçãoes são verdadeiras.
#### 1.3.4 Or:
   * É verdade quando no mínimo umas das proposiçãoes é verdadeira.
      * Mantra da Or: 1 na entrada, 1 na saída.
#### 1.3.5 Nor:
   * É uma Or com uma Not no final.
      * Só é verdade quando todas as proposiçãoes são falsas.
#### 1.3.6 Xor:
   * Só é verdade quando as entradas são diferentes.
#### 1.3.7 XNor:
   * Uma Xor com uma Not no final.
      * Só é verdade quando as duas entradas são iguais.

### 1.4 Circuitos Combinacionais - De Portas Logicas A Um Somador Completo
   * A combinação de portas lógicas é o que realmente dá vida à lógica digital, permitindo construir circuitos incrivelmente complexos a partir de blocos simples como AND, OR e NOT. Para entender como isso funciona e chegar a um somador completo e que é, de fato, a base da ULA - Unidade Lógica e Aritmética, vamos quebrar o processo em etapas:
#### 1.4.1 Meio Somador(Half Adder):
   * Um somador completo é complexo demais para começar, vamos começar com o Meio Somador. Ele soma dois bits de entrada e produz duas saídas:
      * Soma (S): O resultado da soma.
      * Vai Um (Carry Out - CO): Um bit que indica se houve um "vai um" para a próxima posição.
      ![Fonte: @isaulfelipe0]( /arq/img/HalfAdder.PNG "Fonte @isaulfelipe0")
#### 1.4.2 Somador Completo(Full Adder):
   * O Meio Somador é limitado porque não consegue adicionar um "vai um" de uma soma anterior. Para somar números com múltiplos bits - como fazemos no decimal, onde levamos o "vai um" para a próxima coluna.
      * Ele tem três entradas:
         * A: Primeiro bit a ser somado.
         * B: Segundo bit a ser somado.
         * Cin (Carry In): O "vai um" da posição de bit anterior.
      * E Duas saídas:
         * S (Soma): O bit resultante da soma.
         * Cout (Carry Out): O "vai um" gerado que será levado para a próxima posição.
         ![Fonte: @isaulfelipe0]( /arq/img/FullAdderOnlyLogicGates.PNG "Fonte @isaulfelipe0")
         ![Fonte: @isaulfelipe0]( /arq/img/FullAdderWithTwoHalfAdder.PNG "Fonte @isaulfelipe0")
#### 1.4.3 Somadores de Múltiplos Bits (Ripple Carry Adder):
   * Agora que temos um Somador Completo que lida com o "vai um" de entrada, podemos empilhá-los para somarmos dois números - que serão números binarios de 8 bits, que pode representar de -128 a 127 usando complemento de dois para representar números com sinais.
   * Para somar 01001101 + 10111101 precisamos de 8 Somadores Completos.
   * O carry-out de um Somador Completo se torna o carry-in do próximo Somador Completo na sequência.
   ![Fonte: @isaulfelipe0]( /arq/img/RippleCarryAdderWithFull'sAdder's.PNG "Fonte @isaulfelipe0")
### 1.5 Unidade Lógica e Aritmética (ULA)
![Fonte: @isaulfelipe0]( /arq/img/ULA.webp "Fonte @isaulfelipe0")

## 2. O Caminho para a CPU.

### 2.1 Circuitos Sequenciais vs Circuitos Combinacionais:
#### 2.1.1 Circuitos Combinacionais:
   * Em um circuito combinacional, a saída atual depende apenas das entradas atuais. Ele não possui "memória" de estados anteriores.
   * Características:
      * Não armazena informações. O que acontece agora é determinado exclusivamente pelo que está nas entradas agora.
      * Geralmente mais rápidos, pois não há necessidade de estados internos ou sincronização por clock para sua operação básica.
      * Assim que as entradas mudam, as saídas respondem (após um pequeno atraso de propagação das portas lógicas).
      * Exemplos:
         * Portas Lógicas Básicas: AND, OR, NOT, XOR.
         * Somadores como o Meio Somador e o Somador Completo que vimos. O resultado da soma e do carry dependem apenas dos bits que estão sendo somados naquele momento.
         * Decodificadores que convertem um código binário em um sinal de saída único (ex: ativar uma das 4 saídas com base em 2 bits de entrada).
         * Demultiplexadores que seleciona um único dado de entrada para uma das várias saídas disponíveis, com base em bits de seleção.
         * Multiplexadores que selecionam uma de várias entradas para ser roteada para uma única saída, com base em bits de seleção.
#### 2.1.2 Circuitos Sequenciais:
   * Em um circuito sequencial, a saída atual depende das entradas atuais e dos estados anteriores. Eles contêm elementos de memória.
   * Características:
      * Com Memória (Estado Interno): Possuem a capacidade de armazenar bits de informação, lembrando-se de eventos passados. Isso é feito através de elementos de memória como Flip-Flops ou Latches.
      * Sincronização: A maioria dos circuitos sequenciais é síncrona, ou seja, suas mudanças de estado são controladas por um sinal de clock. O clock garante que as mudanças ocorram em momentos específicos e organizados.
      * Saída Depende da Entradas Anteriores: Para saber a saída, você precisa saber não apenas as entradas atuais, mas também das entradas anteriores.
      * Exemplos:
         * Latches e Flip-Flops: São os blocos de construção básicos da memória digital, capazes de armazenar 1 bit de informação.
         * Contadores: Incrementam um valor a cada pulso de clock. A saída depende do valor anterior e do pulso do clock.
         * Registradores: Grupos de Flip-Flops que armazenam palavras binárias (vários bits).
### 2.2 Flip-Flop (a unidade de memória mais básica):
   * #### Flip Flop RS:
      * O FF RS é o tipo mais básico e com o funcionamento mais simples de se entender. O seu nome é devido a suas duas entradas, a Set e a Reset, responsáveis por alterar diretamente os estados das saídas.
      * Tabela Verdade: A tabela verdade de um Flip Flop SR(Set/Reset)
         * ![Fonte: makerhero.com]( /arq/img/FlipFlopSRTruthTable.webp "Fonte makerhero.com")
      * ![Fonte: @isaulfelipe0]( /arq/img/FlipFlopSR.png "Fonte @isaulfelipe0")
      * Ele implementado com portas Nand e Nor esta na pasta arq/circuitos
   * #### Flip Flop JK:
      * O FF JK é um dos mais utilizados, pois diferente do RS ele tem o tratamento para o caso onde S=1 e R=1.
   * Tabela Verdade: A tabela verdade de um Flip Flop JK
      * ![Fonte: makerhero.com]( /arq/img/FlipFlopJKTruthTable.webp "Fonte makerhero.com")
   * ![Fonte: makerhero.com]( /arq/img/FlipFlopJKWithOneFlipFlopSR.webp "Fonte makerhero.com")
   * Por causas das limitações do logisim não foi possiível implementar com portas igual aos outros circuitos.
   * #### Flip Flop T:
      * O FF é T nada mais do que um FF JK com uma única entrada interligadas, implicando que J=K. Como as duas entradas do circuito sempre são iguais, o circuito irá funcionar como um comutador da saída quando a entrada T for 1 e não são encontrado comercialmente, sendo geralmente feito a partir de um FF JK quando se faz necessário.
      * Tabela Verdade: A tabela verdade de um Flip Flop T
         * ![Fonte: makerhero.com]( /arq/img/FlipFlopTTruthTable.webp "Fonte makerhero.com")
      * ![Fonte: @isaulfelipe0]( /arq/img/FlipFlopTWithOneFlipFlopJK.png "Fonte @isaulfelipe0")
      * Por causas das limitações do logisim não foi possiível implementar com portas igual aos outros circuitos.
   * #### Flip Flop D:
      * Parecido com o FF T, o circuito do FF D consiste nas duas entradas interligadas, entretanto uma entrada é sempre o sinal negado da outra, logo J ≠ K. Este circuito é bastante importante e amplamente utilizado na eletrônica para diversos projetos, isso devido ao fato de ele não existir a condição de comutar o estado anterior. Esta característica força o Flip Flop a funcionar como uma memória onde o dado sempre será obtido pela entrada D.
      * Tabela Verdade: A tabela verdade de um flip flop D
         * ![Fonte: instrumentationtools.com]( /arq/img/FlipFlopDTruthTable.webp "Fonte instrumentationtools.com")
      * ![Fonte: @isaulfelipe0]( /arq/img/FlipFlopDWithOneFlipFlopJk.png "Fonte @isaulfelipe0")
      * Por causas das limitações do logisim não foi possiível implementar com portas igual aos outros circuitos.
### 2.3 Como um registrador é feito com vários flip-flops:
   * Existem varios tipos de registradores, agora vou lhe mostrar como os registradores de deslocamento do tipo 1. SISO(Serial-in/serial out) 2. SIPO (serial-In/Parallel-out) 3. PIPO(Parallel-in/Parallel-out) são feitos através de Flip Flops. 
      * SISO: 
      ![Fonte: @isaulfelipe0]( /arq/img "Fonte @isaulfelipe0")
      * SIPO:
      ![Fonte: @isaulfelipe0]( /arq/img "Fonte @isaulfelipe0")
      * PIPO: 
      ![Fonte: @isaulfelipe0]( /arq/img "Fonte @isaulfelipe0")
### 2.4 A Estrutura da CPU: 
   * Imagine que a CPU é como o diretor de uma grande empresa ou o cérebro humano em ação, com funções muito especializadas. Ela é responsável por executar todas as instruções de um programa, desde cálculos simples até a coordenação de tarefas complexas.Imagine que a CPU é como o diretor de uma grande empresa ou o cérebro humano em ação, com funções muito especializadas. Ela é responsável por executar todas as instruções de um programa, desde cálculos simples até a coordenação de tarefas complexas.
   * #### Os três componentes principais trabalham em conjunto para realizar essas operações:
      * ##### Unidade Lógica e Aritmética (ULA):
         * O que é? É o coração numérico e lógico da CPU. É onde as operações matemáticas (como soma, subtração, multiplicação e divisão) e as operações lógicas (como AND, OR, NOT, XOR, e comparações) são realmente executadas.
         * Analogia: Pense na ULA como o gênio da matemática e da lógica do diretor da empresa. Ela não questiona ou planeja; apenas executa os cálculos e comparações que o diretor (Unidade de Controle) manda fazer, com uma velocidade e precisão incríveis. É um trabalhador extremamente eficiente, mas sem iniciativa própria.
         * Função: Recebe dados e uma instrução sobre o que fazer com eles (por exemplo, "somar", "comparar se um é maior que o outro", "aplicar um AND lógico") e produz um resultado.
      * ##### Unidade de Controle:
         * O que é? É o "cérebro do cérebro". A Unidade de Controle coordena TODAS as operações da CPU. Ela interpreta as instruções de um programa (que vêm da memória), gera os sinais de controle necessários para a ULA e os registradores, e sincroniza o fluxo de dados entre os diferentes componentes da CPU e da memória.
         * Analogia: Esta é o próprio diretor da empresa (ou o maestro de uma orquestra). Ele lê o plano de negócios (instrução do programa), decide qual departamento (ULA, Registradores) precisa fazer o quê, em que ordem e quando. Ele envia memorandos (sinais de controle) para garantir que todos trabalhem em sincronia e no momento certo. Sem o diretor, os outros componentes não saberiam o que fazer.
         * Função: Busca instruções na memória, decodifica-as, gera sinais de temporização e controle para dirigir as operações da ULA, controlar o movimento de dados para e dos registradores, e interagir com outros componentes do sistema.
      * ##### Registradores: 
         * O que são? São pequenas e rápidas memórias dentro da própria CPU. Eles armazenam temporariamente dados, instruções e endereços de memória que a CPU precisa acessar de forma muito rápida durante o processamento. São o tipo de memória mais rápido de um computador, mas também o mais caro e com menor capacidade.
         * Analogia: Pense neles como as mesas de trabalho (ou blocos de notas) do diretor e do gênio da matemática. Em vez de ir buscar um arquivo no almoxarifado (memória RAM) toda hora, eles mantêm os documentos e números mais importantes e frequentemente usados bem à mão, em suas mesas. Isso agiliza muito o trabalho.
         * Função: 
            * Registradores de Uso Geral: Armazenam dados que estão sendo processados pela ULA.
            * Contador de Programa (PC - Program Counter): Guarda o endereço da próxima instrução a ser executada.
            * Registrador de Instrução (IR - Instruction Register): Armazena a instrução que está sendo decodificada e executada no momento.
            * Acumulador: Armazena resultados intermediários de operações da ULA.
            * Esses três componentes trabalham em um ciclo contínuo: a Unidade de Controle busca uma instrução, a coloca em um Registrador, a Unidade de Controle a decodifica e instrui a ULA a performar uma operação em dados que também estão nos Registradores, e o resultado é novamente armazenado em um Registrador. Essa orquestração eficiente é o que permite que a CPU execute milhões ou bilhões de operações por segundo, dando vida ao computador.
   * #### O Ciclo de Instrução:
      * O Ciclo de Instrução - também conhecido como ciclo Fetch-Decode-Execute, ou Busca-Decodifica-Executa - é o processo fundamental que a CPU repete incessantemente, e é o que amarra o papel da Unidade de Controle, dos Registradores e da ULA
         * ##### Passo 1: Busca (Fetch)
            * O objetivo é trazer a próxima instrução do programa da memória principal (RAM) para a CPU.
            * 1. PC → MAR: O endereço da próxima instrução a ser executada é copiado do Contador de Programa (PC) para o Registrador de Endereço de Memória (MAR).
            * 2. Busca na Memória: A Unidade de Controle envia um sinal de Leitura pela linha de controle. O MAR usa o endereço para localizar a instrução na RAM, e a instrução é colocada no Barramento de Dados.
            * 3. Memória → IR: A instrução é copiada do Barramento de Dados para o Registrador de Instrução (IR).
            * 4. PC + 1: O Contador de Programa (PC) é incrementado para apontar para o endereço da próxima instrução.
         * ##### Passo 2: Decodificação (Decode)
            * O objetivo é interpretar a instrução que acabou de ser buscada e preparar o circuito para executá-la.
            * 1. IR → UC: A instrução (agora no Registrador de Instrução - IR) é enviada à Unidade de Controle (UC).
            * 2. Interpretação: A UC analisa o código de operação (opcode) da instrução (ex: ADD, MOVE, JUMP).
            * 3. Geração de Sinais: Com base no opcode, a UC gera todos os sinais de controle necessários. Ela define:
               * Quais Registradores fornecerão os dados de entrada.
               * Qual operação a ULA deverá realizar.
               * Onde o resultado deverá ser armazenado (em qual Registrador ou endereço de Memória).
         * ##### Passo 3: Execução (Execute)
            * O objetivo é realizar a operação real especificada pela instrução decodificada.
            * 1. Movimentação de Dados: Os dados necessários para a operação são movidos dos Registradores para as entradas da Unidade Lógica e Aritmética (ULA).
            * 2. Operação da ULA: A UC ativa a ULA e envia o sinal de controle específico para a operação (ex: sinal SOMA). A ULA realiza a operação.
            * 3. Armazenamento de Resultado: O resultado da ULA é enviado ao Barramento de Dados e, tipicamente, armazenado de volta em um Registrador de uso geral (como o Acumulador) ou em um endereço de memória.
            * 4. Verificação de Flags: O estado da ULA é checado para atualizar os flags (como Zero, Negativo ou Vai Um) no Registrador de Estado da CPU.
      * Após a etapa de Execução, o ciclo se repete, começando novamente com a Busca da instrução apontada pelo PC (que já foi incrementado no Passo 1). Esse loop incessante é a força motriz de todo o software em execução.
## 3. Organização do Computador.
### 3.1 Hierarquia de Memória:
   * A utilização de vários tipos de memória em um computador é um pilar da arquitetura moderna, conhecida como Hierarquia de Memória.
   * O motivo para essa complexa estrutura é simples: não é financeiramente viável construir uma única memória que seja simultaneamente grande, rápida e barata.
   * O princípio por trás da hierarquia é maximizar o desempenho (velocidade) com o menor custo possível, explorando a Localidade de Referência - a tendência de o processador precisar acessar os mesmos dados e instruções repetidamente, ou dados próximos na memória.
   * #### 3.1.1 Memória Cache (L1, L2, L3)
      * Propósito: Acelerar a CPU
      * Função: Atuar como uma "área de espera" super-rápida entre a CPU e a RAM. Ela armazena cópias dos dados e instruções que a CPU tem usado mais frequentemente ou que provavelmente usará em seguida.
      * Velocidade: É construída com tecnologia SRAM (RAM Estática), que é muito mais rápida que a DRAM (usada na RAM), mas também muito mais cara e requer mais espaço físico.
      * Localização: Geralmente embutida dentro do próprio chip do processador (L1 e L2) ou muito próxima a ele (L3).
   * #### 3.1.2 Memória Principal (RAM - Random Access Memory)
      * Propósito: Área de Trabalho do Sistema
      * Função: É a "mesa de trabalho" do computador. Armazena temporariamente o sistema operacional, todos os programas abertos e os dados que estão sendo processados no momento.
      * Velocidade: É o equilíbrio entre velocidade e capacidade, sendo muito mais lenta que a Cache, mas infinitamente mais rápida que o armazenamento secundário.
      * Volatilidade: É volátil. Se a energia for cortada (você desliga o PC ou acaba a luz), todos os dados na RAM são perdidos.
      * Tecnologia: Usa chips DRAM (RAM Dinâmica), que são mais baratos e têm maior densidade (mais capacidade), mas são mais lentos.
   * #### 3.1.3 Armazenamento Secundário (HDD ou SSD)
      * Propósito: Armazenamento Permanente
      * Função: Armazenamento de longo prazo para o sistema operacional, programas, arquivos e dados que não estão em uso no momento. É onde o sistema busca as informações para serem carregadas na RAM.
      * Velocidade: É o nível mais lento de memória (especialmente o HDD, que é mecânico), pois a prioridade aqui é a capacidade e a não volatilidade. O SSD, usando memória Flash, é significativamente mais rápido que o HDD, mas ainda lento em comparação com a RAM e a Cache.
      * Não Volatilidade: Os dados persistem mesmo sem energia.
      * Capacidade/Custo: Possui a maior capacidade e o menor custo por gigabyte.
   * #### 3.1.4 Por Que Essa Hierarquia Funciona?
      * A hierarquia é uma solução de engenharia baseada na observação de que o processador tende a reutilizar dados.
         * 1. Quando a CPU precisa de um dado:
            * Ela primeiro procura na Cache (mais rápido, mais próximo).
            * Se não estiver lá (Cache Miss), ela busca na RAM.
            * Se não estiver na RAM (o programa ainda não está carregado), ela busca no Disco/SSD.
         * 2. O Princípio da Cópia: Quando o dado é encontrado em um nível mais baixo (lento), ele é copiado não apenas para o processador, mas também para os níveis mais altos (mais rápidos) da hierarquia (RAM → Cache), garantindo que, se o dado for necessário novamente, ele estará disponível mais rápido.
      * Essa estratégia faz com que o sistema, como um todo, funcione com uma velocidade média próxima à da Cache, mas com um custo médio próximo ao do Disco/SSD, otimizando o desempenho pelo menor preço.
### 3.2 Barramentos:
   * Um barramento é um conjunto de linhas de comunicação (fios ou trilhas na placa-mãe) compartilhadas por vários componentes do sistema. Eles são responsáveis por transferir informações (dados, endereços e comandos de controle) entre os módulos do computador.
   * Eles são divididos em três grupos funcionais principais, cada um com sua própria função na "estrada":
   * #### 1. Barramento de Endereços (Address Bus)
      * Função: Determinar a Origem/Destino
      * O que faz: Leva o endereço de memória (RAM) ou de um dispositivo I/O que a CPU deseja acessar.
   * #### 2. Barramento de Dados (Data Bus)
      * Função: Transportar a Informação Real
      * O que faz: Transporta os dados propriamente ditos, seja uma instrução do programa sendo lida da memória, seja um resultado de uma operação da ULA sendo gravado, ou dados de um periférico (como um teclado ou mouse).
   * #### 3. Barramento de Controle (Control Bus)
      * Função: Coordenar e Gerenciar o Tráfego
      * O que faz: Transporta sinais de controle (comandos) e de temporização (sincronização) gerados pela Unidade de Controle (UC) da CPU para todos os outros módulos. Ele gerencia o fluxo de informações para evitar conflitos.