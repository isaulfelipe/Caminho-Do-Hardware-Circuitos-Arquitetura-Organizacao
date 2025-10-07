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
#### 1.2.2 Conversão Decimal-Binário para Números <= 0:
   * Pegue o modulo do numero que você quer converter de decimal para binario e faça o topico 1.2.1 normalmente com o modulo desse numero, após isso basta apenas repetir os números até encontrar o primeiro 1 e depois trocar todos os 1 por 0 e 0 por 1.
#### 1.2.3 Conversão Binário-Decimal para Números >= 0: 
![Fonte: @isaulfelipe]( /arq/img/ConversaoBinarioDecimalParaNumerosPositivos.png "Fonte @isaulfelipe")
#### 1.2.4 Conversão Binário-Decimal para Números <= 0: 
   * Primeiro pega o modulo desse número negativo (se -44, o modulo da 44), após isso, faça o topico 1.2.3 com o modulo desse número e depois ponha o sinal de negativo(-).
   
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

### 1.4 Circuitos Combinacionais
   * A combinação de portas cria circuitos mais complexos, como um somador completo e que é a base da ULA.
#### 1.4.1 De Portas Logicas A Um Somador Completo
   * A combinação de portas lógicas é o que realmente dá vida à lógica digital, permitindo construir circuitos incrivelmente complexos a partir de blocos simples como AND, OR e NOT. Para entender como isso funciona e chegar a um somador completo e que é, de fato, a base da ULA - Unidade Lógica e Aritmética, vamos quebrar o processo em etapas:
      * Um somador completo é complexo demais para começar, então vamos primeiro a algo mais simples: o Meio Somador (Half Adder). Ele soma dois bits de entrada (A e B) e produz duas saídas:
         * Soma (S): O resultado da soma.
         * Vai Um (Carry Out - CO): Um bit que indica se houve um "vai um" para a próxima posição.
         ![Fonte: @isaulfelipe]( /arq/img/HalfAdder.PNG "Fonte @isaulfelipe")