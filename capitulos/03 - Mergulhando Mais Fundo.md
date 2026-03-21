# Mergulhando Mais Fundo

Olá de novo, marujo! Chegou a hora de navegarmos em direção a mares mais profundos, pois é lá onde se encontram os tesouros mais antigos e as criaturas mais raras. Sério, olha esse bixo:

![Peixe morcego dos lábios vermelhos](../imagens/03_peixe_morcego.png)

Neste capítulo, aprenderemos sobre ferramentas importantíssimas que tornam C uma linguagem completa e prática:

- Funções
- Estruturas
- Ponteiros
- Diretivas de pré-processamento
- Cabeçalhos

## Funções

Funções são um construto de linguagens de programação que servem dois propósitos principais **importantíssimos**: redução de código duplicado e organização de código. É essencial que você mantenha estes propósitos em mente até que eles sejam internalizados, pois como você perceberá ao decorrer da vida, criar boas funções é o caminho para escrever programas lindos no paradigma procedural.

Ok, nós sabemos o motivo de ser das funções, mas o que são elas de fato? A ideia geral é dar um nome para um **bloco de código**. Isto alcança os objetivos citados acima da seguinte forma:

### Redução de código duplicado

Vamos supor que você tem uma sequência de ações que é muito comum em seu programa. Por exemplo, a sequência de passos (linhas de código) que representa a ação "pescar" (bloco de código) pode ser:

1. Botar a rede no mar
2. Cercar o peixe
3. Bater o remo
4. Puxar a corda
5. Colher a rede

Assim como na boa e velha música [Canoeiro](https://www.youtube.com/watch?v=Q10NERSv2og&list=RDQ10NERSv2og&start_radio=1), de Dorival Caymmi. Já que esta ação "pescar" é muito comum no seu código, seria bom se não precisássemos reescrever todos estes passos de novo e de novo... E é aí que as funções chegam para o resgate. Criando uma função chamada `pescar` que englobe estes 5 passos, nós podemos em nosso programa escrever apenas uma linha dizendo "execute o passo a passo da pescaria" onde antes precisaríamos descrever o passo a passo inteiro. Em termos de pseudocódigo bem brando, a diferença pode ser ilustrada assim, primeiro sem o uso de funções:

```
// pescando pela primeira vez
Botar rede no mar
Cercar peixe
Bater o remo
Puxar corda
Colher rede

// dando um fim digno ao peixe
Cozinhar peixe
Comer peixe

// pescando de novo... muita repetição
Botar rede no mar
Cercar peixe
Bater o remo
Puxar corda
Colher rede

// mostrando misericórdia ao peixe
Jogar peixe no mar
```

E agora _com_ o uso de funções

```
// definindo nossa função
função pescar() {
    Botar rede no mar
    Cercar peixe
    Bater o remo
    Puxar corda
    Colher rede
}

// pescando através da nossa função
pescar()

Cozinhar peixe
Comer peixe

// dessa vez há muito menos código duplicado!
pescar()

Jogar peixe no mar
```

Pode parecer que a diferença não foi muita, mas imagine que nosso código é muito maior que isso e que ele envolve pescar umas 100 vezes. Sem funções, teríamos 500 linhas desnecessariamente repetidas, com chances ainda de haver inconsistências entre as repetições, pois nós somos [apenas humanos](https://youtu.be/L3wKzyIN1yk?si=8VHnW1c6BpR7TYB6), e podemos esquecer de incluir a instrução "Bater o remo" sem querer.

Há algumas coisas que podem ter te gerado dúvida neste pseudocódigo, então deixe-me esclarecer alguns pontos:

1. **Ordem de execução**: como sabemos, programas são executados linha a linha, de cima para baixo. É importante notar que as primeiras linhas do segundo pseudocódigo representam apenas a _definição_ da função, ou seja, nós estamos apenas dando um nome para um bloco de código - este bloco de código NÃO é executado. Já nas linhas escritas "pescar", ocorre um desvio na execução do programa; um salto para as linhas de código que compõem a função `pescar`. Fazer este desvio, ou seja, dizer "execute esta função", é o que chamamos de **chamar uma função**. Quando a função termina de executar, retornamos para a linha na qual ela foi chamada, e continuamos a execução do programa a partir dali.
2. **Sintaxe ()**: na maioria das linguagens, ao definirmos uma função, o nome dela é seguido de parênteses, e dentro destes parênteses é onde colocamos os parâmetros que a função recebe (explicaremos o que são parâmetros daqui a pouquinho). Agora, quando chamamos uma função, também colocamos parênteses imediatamente após o nome da função, e dentro deles colocamos os argumentos que passamos à ela.

Ok, espero ter conseguido te mostrar como funções reduzem código duplicado sem te dar uma dor de cabeça. Só para acabar esta parte, vou encerrar com uma reflexão par você manter em mente. É muito comum programadores ficarem aversos a duplicações, e irem a extremos para **eliminar** todas elas. Com isso, surgiu o princípio DRY (Don't Repeat Yourself - Não se repita), que possui um nome bem auto-explicativo. No entanto, ficar tão neurado com duplicações não é exatamente um caminho mágico para bons códigos. Pessoas engraçadas que perceberam isso criaram um princípio diferente, chamado [WET](https://dev.to/wuz/stop-trying-to-be-so-dry-instead-write-everything-twice-wet-5g33) (Write Everything Twice - Escreva tudo duas vezes), defendendo a pauta de que está tudo bem ter alguns pedaços de código duplicados, o problema geralmente surge quando há algo se repetindo 3+ vezes.

Enfim, chega, bora ver como funções ajudam também na organização de código.

### Organização de código

Vamos pensar em uma nova situação. Digamos que você está escrevendo um programa que faz muitas coisas diferentes, como:

1. Calcular a direção e velocidade do vento
2. Avaliar a calmaria do mar
3. Girar o mastro
4. Alinhas as velas
5. Calcular rota para a ilha mais próxima

E também suponhamos que cada uma dessas coisas se consiste em uma lista de muitos passos. Se nós não dividirmos nosso código em funções, ou seja, colocarmos todas as instruções individuais diretamente no `main`, isto faria com que ele ficasse extremamente poluído. Dessa forma, quando quiséssemos alterar algum procedimento, teríamos que ficar procurando uma linha específica em meio a um `main` enorme. O que gostariamos de fazer é **abstrair** os detalhes de cada procedimento, e apenas colocar no main as instruções mais gerais. Para fazer isso, colocamos o bloco de código com os detalhes de como calcular a direção do vento em uma função chamada `calcula_velocidade_do_vento` (nomear coisas is my passion), e o mesmo vale para as demais tarefas. No fim, nosso `main` ficará limpinho assim:

```
main() {
    calcula_velocidade_do_vento()
    avalia_calmaria()
    gira_mastro()
    alinha_velas()
    calcula_rota()
}
```

Obviamente, nem tudo precisa ser colocado dentro de funções, e o `main` não precisa consistir apenas de chamadas de funções.

Falando em `main`, você provavelmente já deve ter notado pelos parênteses que ele também é uma função! O `main` é uma função especial, pois ele é por padrão a primeira função que é chamada na execução de um programa.

O fato de o `main` ser uma função também nos revela um fato muito relevante: **podemos chamar funções dentro de funções**. Inclusive, podemos chamar uma função dentro dela mesma - é o que chamamos de **recursão** - mas não vamos nos aprofundar nisso nesta trilha.

### Parâmetros, argumentos e valor de retorno

Até agora as funções que demos de exemplo têm sido meio bestas, pois elas apenas fazem sempre a mesma coisa; não aceitam nenhum _input_. Se você pensar no conceito de uma função matemática, ela pega um ou mais valores e então gera um resultado com base nestes valores. Por exemplo: a função `f(x, y) = x² + y²` toma dois números como _argumento_ e então _retorna_ um único número como resultado. Na programação, podemos fazer o mesmo.

Na verdade, na programação as coisas são ainda melhores, pois nossas funções podem aceitar como input não apenas números, mas sim valores de qualquer tipo. Se você quiser criar uma função que recebe como input o nome de um peixe e retorna o nome do melhor tipo de isca para aquele peixe, você pode!

Para podermos ver a coisa na prática, vamos antes definir melhor cada termo:

- **Parâmetros**: são os inputs que uma função aceita. Por exemplo, em "`f(x, y)`", os parâmetros são `x` e `y`.
- **Argumentos**: são os valores que passamos para uma função ao chamá-la. É fácil de confundir parâmetro com argumento, por conta disso esses termos são usados de forma intercambiável em muitos cenários. Em `f(2, 5)`, os argumentos são `2` e `5`.
- **Retorno**: é o valor que uma função gera como output. Usando a função `f(x, y) = x² + y²` como exemplo, o valor de retorno passando `2` e `5` como argumento seria `29`. No C, usamos a palavra-chave `return` no corpo de uma função para fazer ela retornar um valor.

### Funções na prática

No C, a sintaxe para definir uma função é relativamente simples. Escrevemos primeiro o tipo do valor de retorno da função, depois o nome da função, seus argumentos (com tipo e nome) e por fim, colocamos o corpo da função entre chaves. Aqui vai um exemplo:

``` C
float pesarPeixe(float volume, float densidade) {
    float peso = volume * densidade;
    return peso;
}
```

Aqui, a função se chama `pesarPeixe`, e tanto o valor de retorno quanto os parâmetros (`volume` e `densidade`) são do tipo `float`.

Vejamos outro exemplo:

``` C
void cumprimentarPeixe(char *nomePeixe, bool superCumprimento) {
    if(superCumprimento) {
        printf("MUITO PRAZER SENHOR PEIXE %s!!!\n", nomePeixe);
    } else {
        printf("olá, %s!\n", nomePeixe);
    }
}
```

Dessa vez, o nome da função é `cumprimentarPeixe`, seus argumentos são uma string (`char *`) e um `bool`. Contudo, dessa vez a função não possui um valor de retorno, e para indicar isto colocamos o tipo do retorno como `void`.

Uma coisa que você precisa ter em mente é que a ordem na qual definimos as funções importa. Se definirmos estas funções antes do `main`, podemos chamá-las lá dentro sem problema:

``` C
#include <stdio.h>
#include <stdbool.h>

float pesarPeixe(float volume, float densidade) {
    float peso = volume * densidade;
    return peso;
}

void cumprimentarPeixe(char *nomePeixe, bool superCumprimento) {
    if(superCumprimento) {
        printf("MUITO PRAZER SENHOR PEIXE %s!!!\n", nomePeixe);
    } else {
        printf("olá, %s!\n", nomePeixe);
    }
}

int main() {
    float pesoLambari = pesarPeixe(1000, 6);
    cumprimentarPeixe("Lambari", true);
    printf("Você pesa %.0f gramas, Lambari.\n", pesoLambari);
    return 0;
}
```

Contudo, se você colocar o main acima das funções, receberá um erro muito camarada, como este aqui:

``` sh
error: conflicting types for ‘pesarPeixe’; have ‘float(float,  float)’
```

O erro não explica muito bem o que está acontecendo exatamente (como muitas vezes é o caso com o C), mas o que está acontecendo é relativamente simples. Ao chegar na linha que chama `pesarPeixe`, o compilador não reconhece este nome, e infere um tipo a ele. Mais tarde, ao chegar de fato na definição da função, ele descobre que o tipo que tinha inferido para a função não bate com o tipo verdadeiro - causando um erro.

Isto significa que o `main` precisa ser a última função e todas as demais precisam ser definidas antes dele? **NÃO!!!** Na verdade, o que podemos fazer se quisermos deixar o main no topo do nosso programa (que é uma boa prática) é **declarar** o _protótipo_ de nossas funções antes do `main`, mas apenas **definir** a função depois dele. Para entender esta afirmação precisamos entender a diferença técnica entre os termos "definir" e "declarar":

- **Definir**: é dizer qual é o valor de algo. No caso de funções, é dizer o bloco de código que a compõe.
- **Declarar**: é apenas dizer ao compilador "esse treco existe e o tipo dele é X". No caso de funções, precisamos dizer apenas o nome dela, o tipo de retorno e o tipo dos parâmetros.

Ou seja, o "truque" (akshually não é um truque, é parte do design da linguage, e se chama _forward declaration_) é colocar apenas o **protótipo** (ou tipo) das funções antes do `main`. Aqui vai um exemplo usando as funções fantásticas de agora pouco:

``` C
#include <stdio.h>
#include <stdbool.h>

// forward declaration
float pesarPeixe(float volume, float densidade);
void cumprimentarPeixe(char *nomePeixe, bool superCumprimento);

// main no topo
int main() {
    float pesoLambari = pesarPeixe(1000, 6);
    cumprimentarPeixe("Lambari", true);
    printf("Você pesa %.0f gramas, Lambari.\n", pesoLambari);
    return 0;
}

// definição das funções

float pesarPeixe(float volume, float densidade) {
    float peso = volume * densidade;
    return peso;
}

void cumprimentarPeixe(char *nomePeixe, bool superCumprimento) {
    if(superCumprimento) {
        printf("MUITO PRAZER SENHOR PEIXE %s!!!\n", nomePeixe);
    } else {
        printf("olá, %s!\n", nomePeixe);
    }
}
```

Se você rodar este código, verá que tudo dá certo e que o mundo é maravilhoso.

Enfim, já deu de falar sobre funções, já nos prolongamos demais neste assunto. Partiu falar de algo menos interessante: _structs_!!!

## Estruturas

Você já se pegou pensando "NÓÓóóóssssaaaa.... a tipagem do C é muito limitante"? Pois é, foi o que pensei. Afinal de contas, o C como o vimos até agora basicamente só nos permite representar números, booleanos, caracteres e listas. E se nós quisermos representar, digamos, um BARCO?! Para fazer isso, precisaríamos de alguma forma representar seus atributos, como seu nome, sua velocidade máxima, o número de velas, e qualquer outra coisa que você queira. A forma de fazer isso é usando **structs** (estruturas). No C, você pode agregar valores em uma estrutura da seguinte forma:

``` C
struct Barco {
    char *nome;
    float velocidade_maxima;
    int numero_velas;
};
```

Cada um dos itens dentro das chaves é um **atributo** ou **campo** da estrutura. Aqui, estamos criando uma espécie de "molde" para barcos, mas não estamos criando nenhum barco específico. Para criar um barco de verdade, precisamos fazer o seguinte:

``` C
struct Barco nosso_barco = {.nome = "Sea of C", .velocidade_maxima = 130.0f, .numero_velas = 16};
```

> O nome dos atributos pode ser omitido. Ou seja, você poderia só escrever `struct Barco nosso_barco = {"Sea of C", 130.0f, 16};`.

Agora sim temos um barco de verdade! Para acessar seus atributos, escrevemos o nome da variável seguida de um ponto e então o nome do atributo, tipo assim:

``` C
nosso_barco.numero_velas
```

Sendo assim, podemos modificar os atributos do barco após ele ter sido definido facilmente:

``` C
// definição inicial
struct Barco nosso_barco = {"Sea of C", 130.0f, 16};
// modificando um atributo
nosso_barco.numero_velas = 8;
```

Perceba também que o tipo da nossa variável `nosso_barco` é `struct Barco`. Contudo, podemos utilizar a palavra-chave `typedef` para simplificar mais este tipo para apenas `Barco`. Fazer isto é fácil, ao invés de declararmos a estrutura como fizemos agora pouco, usamos essa sintaxe aqui:

``` C
typedef struct {
    char *nome;
    float velocidade_maxima;
    int numero_velas;
} Barco;
```

E simples assim, conseguimos usar o tipo `Barco` como se ele fosse um `int` ou um `char`:

``` C
Barco nosso_barco = {"Sea of C", 130.0f, 16}
```

Usando `typedef` ou não, você pode passar estruturas como argumento ou valor de retorno de funções. Tente escrever um programa que faz isso para ver com seus próprios óios.

## Ponteiros

Chegou a hora de falar dos tão temidos ponteiros. No imaginário compartilhado da bolha de estudantes iniciantes de programação, existe a noção de que ponteiros são um conceito muito difícil de ser compreendido. Contudo, vou tentar te mostrar agora que não tem motivos para temê-los. De muitas formas, ponteiros são como ursos e tigres, eles parecem ameaçadores mas na verdade são super dóceis e você deveria tentar fazer carinho neles ao encontrá-los na natureza.

Irei direto ao ponto - o que é um ponteiro? A resposta é: **um endereço de memória**. Você lembra que a memória é como uma prateleira com vários cubículos, em que cada cubículo tem um endereço e armazena um dado? Então, o ponteiro é o endereço.

Toda variável que usamos em nossos programas fica em algum lugar da prateleira (memória), e as vezes saber o endereço da variável pode ser útil; é para isso que usamos ponteiros. E digo mais, como tudo em nossos computadores, endereços de memória são apenas números. Ou seja, ponteiros são basicamente um número indicando uma _posição_ na memória.

> Por convenção, representamos números que estão agindo como ponteiros como hexadecimal. Em C, para representar um número hexadecimal colocamos o prefixo `0x` no número. Ou seja, em questão de valor, `10` é a mesma coisa que `0xA`, e `32` é a mesma coisa que `0x20`.

Pelas minhas observações extremamente científicas, a confusão que as pessoas sentem em relação a ponteiros emergem de 3 fontes principais:

1. Não entenderem a representação lógica da memória do computador;
2. Por terem sido condicionadas a acharem que ponteiros são um conceito difícil, ficam procurando um "algo a mais" para ser entendido, sendo que na verdade não tem muita magia não;
3. Ficarem confusas ao ver a sintaxe do C para a manipulação de ponteiros.

A fonte 1 provavelmente não será um problema se você leu o [capítulo 00](https://github.com/ConwayUSP/Sea-of-C/blob/main/capitulos/00%20-%20Antes%20de%20Zarparmos.md#org33f335a) com carinho. A fonte 2 é psicológica, então só pode ser resolvida com anos de terapia. Já a fonte 3, irei tentar mitigar com calma a partir de agora.

No C, usamos 2 símbolos para brincar com ponteiros: o `*` e o `&`. Estes símbolos são complementares - eles fazem coisas opostas.

- `&`: ao colocarmos este símbolo antes do nome de uma variável em alguma expressão, estamos pegando o **endereço** daquela variável. Ou seja, se tenho uma variável `int tamanho_barco = 300` que está armazenada no endereço `0x8000` da memória, a expressão `&tamanho_barco` irá gerar o valor `0x8000`.
- `*`: é usado para _derreferenciar_ um ponteiro. Ponteiros são também chamados de **referências**, então **derreferenciar** significa que dado um endereço de memória (ponteiro), obtemos o valor para o qual ele aponta. Logo, supondo que temos uma variável armazenando o endereço `0xFFF0` chamada `ponteiro_maritimo`, a expressão `*ponteiro_maritimo` geraria o valor da variável que está na posição `0xFFF0` da memória.

Até agora deve estar tudo tranquilo. A confusão surge porque na verdade o `*` é usado em mais uma situação: na definição do tipo de uma variável/argumento como sendo um ponteiro. Se quisermos declarar uma variável como sendo o endereço de um valor do tipo `int`, dizemos que o tipo do ponteiro é `int *`. Aqui vai um exemplo completo:

``` C
// variável do tipo int
int peso_atum = 2;

// endereço (ponteiro) da variável de tipo int
int *ptr_peso_atum = &peso_atum;

// derreferenciando o ponteiro para ter acesso ao valor da variável
*ptr_peso_atum = 3;
```

Encare um pouco este código e tenha certeza de que entende ele. A linha mais importante de ser compreendida é a segunda. Nela, combamos a sintaxe `int *` com a sintaxe `&peso_atum`. O `int *` nos garante que o tipo da variável `ptr_peso_atum` é "ponteiro para `int`", e o `&peso_atum` nos garante que estamos inicializando aquela variável para ser o endereço de `peso_atum`.

Na última linha, estamos "seguindo" o ponteiro até o endereço de memória onde está `peso_atum` - pode ser por exemplo o endereço `0x123`. Além de seguirmos até lá, estamos **modificando** o conteúdo que está armazenado naquela posição (usando o `= 3`). Ou seja, se você der um `printf()` no valor de `peso_atum` antes da última linha, o resultado será `2`, mas se der o print depois, o resultado será `3`.

Ok, falamos e falamos e onde isto nos levou? A lugar nenhum... nós já sabíamos como modificar o valor de uma variável, em uma linha só, inclusive!! Bom, é verdade, mas o verdadeiro poder dos ponteiros se revela _principalmente_ quando passamos eles como argumentos para funções.

Deixe-me explicar melhor. Digamos que você tem uma função que deve ser capaz de _modificar_ uma variável que é passada como argumento (um `int`, por exemplo). Um jeito que você poderia tentar fazer isto é:

``` C
// função que "modifica" um número
int aumentarBarco(int tamanho_atual) {
    tamanho_atual += 5;
}

// usando ela
int tamanho_barco = 10;
aumentarBarco(tamanho_barco);
```

Que valor você acha que seria exibido se você desse `printf` no valor de `tamanho_barco` no fim deste programa? Bom, tudo que a função `aumentarBarco` faz é aumentar o valor do argumento que foi passado em 5 unidades. Como nós passamos `tamanho_barco` (`10`) como argumento, faria sentido que após a chamada da função, ele passasse a valer `15`. Entretanto, se você acha que `tamanho_barco` vale `15` ao final do programa, você infelizmente nunca esteve tão _brutalmente_ errado.

O problema aqui é que quando passamos um valor como argumento para uma função, o argumento (no nosso caso `tamanho_atual`) armazena apenas uma **cópia** do valor que foi passado (`tamanho_barco`). Contudo, `tamanho_atual` e `tamanho_barco` são **variáveis diferentes**, possuem **endereços diferentes** e **escopos diferentes**. Sendo assim, quando dizemos `tamanho_atual += 5` estamos modificando apenas a variável `tamanho_atual` - esta mudança não é refletida no `tamanho_barco`, ele continua valendo `10`.

Se quisermos modificar uma variável **de verdade** usando uma função, vamos ter que usar ponteiros. A ideia é a seguinte: se passarmos como argumento para a função o **endereço** de uma variável, podemos derreferenciar este endereço e modificar o valor que está armazenado na posição indicada por ele. Aqui vai uma correção do exemplo anterior:

``` C
// agora sim :)
void aumentarBarco(int *tamanho_atual) {
    *tamanho_atual += 5;
}

int tamanho_barco = 10;
aumentarBarco(&tamanho_barco);
```

Perceba que estamos usando as sintaxes daquelas 3 formas possíveis:

1. `int *` para indicar que o argumento da função é um ponteiro para `int`
2. `*tamanho_atual` para derreferenciar um ponteiro e acessar o local de memória para onde ele aponta
3. `&tamanho_barco` para pegar o endereço da variável

E dessa forma, se printarmos o valor de `tamanho_barco` ao fim do programa, iremos obter `15`.

Para concluir esta seção, irei apenas te reafirmar que ponteiros são uma coisa bem simples: um endereço de memória. Saiba também que esta utilidade dos ponteiros que te mostrei não é a única - eles também são muito úteis para definir diversas estruturas de dados, mas não iremos nos aprofundar nisso agora.

## Diretivas de pré-processador

Para dar sequência a este longo capítulo, vamos para um tema mais leve: as **diretivas de pré-processador**. O pré-processamento é uma etapa da compilação que ocorre antes da tradução do código para o assembly. A principal função desta etapa é justamente analisar algumas diretivas que você pode incluir em seu código e alterar o código-fonte antes de passar ele para as próximas etapas da compilação.

As diretivas de pré-processador são comandos que começam geralmente com `#`. O `#include` que temos visto sendo usado para importar bibliotecas (como o `stdio.h`) é um exemplo de diretiva. Aqui vai uma listinha delas com uma pequena descrição:

- `#include`: inclui uma biblioteca em nosso programa. Na prática, o que ele faz é copiar o conteúdo daquela biblioteca e colar no lugar da diretiva.
- `#define`: define um termo associado a um valor constante que pode ser usado ao longo do programa. Durante o pré-processamento, todas as ocorrências do termo serão substituídas pelo valor associado.
- `#undef`: desfaz a definição de um termo definido anteriormente.
- `#ifdef`: inicia a delimitação de um bloco de código que só é executado se um certo termo estiver definido.
- `#ifndef`: inicia a delimitação de um bloco de código que só é executado se um certo termo _não_ estiver definido.
- `#endif`: delimita o fim de um bloco condicional iniciado por uma das últimas duas diretivas.

Como você já deve estar habituado a ver o `#include` no topo dos programas, vou pular dar um exemplo dele. Ao invés disso, vejamos um exemplo usando as demais diretivas:

``` C
// ocorrências de "VELOCIDADE_VENTO" serão substituídas por 200
#define VELOCIDADE_VENTO 200

// será executado, pois acabamos de definir VELOCIDADE_VENTO
#ifdef VELOCIDADE_VENTO
    printf("Puxa vida, como o vento está forte hoje! Está a %d km/h\n", VELOCIDADE_VENTO);
#endif

// deletando a definição de VELOCIDADE_VENTO
#undef VELOCIDADE_VENTO

// também irá executar, pois estamos checando se o termo NÃO existe
#ifndef VELOCIDADE_VENTO
    printf("Ufa... passou!");
#endif
```

> Por convenção, termos definidos com `#define` costumam ser escritos com todas as letras maiúsculas.

E é basicamente isso, não há muito mais o que se dizer sobre estas diretivas. Usamos elas geralmente para definir constantes (valores que nunca mudam) e para fazer **header guards**, como veremos daqui a pouquinho.

## Cabeçalhos

Os cabeçalhos (ou _headers_), são arquivos com a extenção `.h` nos quais costumamos colocar declarações de funções, estruturas e variáveis dos módulos de um programa. 

Como você deve estar ciente, a linguagem C já vem com alguns headers por padrão, contendo funções extremamente úteis para várias situações. Contudo, a parte boa dos cabeçalhos é que nós podemos facilmente criar os nossos próprios.

Em qualquer projeto minimamente ambicioso, sentiremos a necessidade de dividir e organizar nosso código em diversos arquivos (dezenas, e as vezes centenas deles). Para podermos compartilhar funções e estruturas entre estes arquivos, é muito conveniente colocarmos elas em headers, pois assim podemos simplesmente usar o `#include` para ter acessá-las de qualquer arquivo `.c`.

Digamos, por exemplo, que nosso SGBD (Sistema Gerador de Barcos Deslumbrantes) precisa utilizar as seguintes coisas em diferentes arquivos:

- Uma estrutura `barco`
- Uma função `comparaBarcos`, que recebe dois barcos e nos diz qual é o mais dinâmico
- Um enum `tipoDeBarco`, que lista diferentes tipos de navegações suportadas por nosso sistema

Bora também dizer que os arquivos necessários do nosso programa são apenas 2 (para não complicar d+ o exemplo). Um dos arquivos será nosso `main.c`, e o outro será o `comparador.c` - que é onde colocaremos a definição da função `comparaBarcos`. Isso mesmo, a definição da função não ficará no cabeçalho, releia o primeiro parágrafo desta seção e perceba a nuance: o cabeçalho costuma conter apenas as **declarações** (ou seja, os protótipos) das funções. Mas chega de papo, vamos ver como fazemos isto na prática. Comecemos pelo cabeçalho - crie um arquivo chamado `barcos.h` na pasta do seu projeto:

``` C
#ifndef BARCOS_H
#define BARCOS_H

enum tipoDeBarco {
    VELEIRO,
    CANOA,
    IATE,
    PESQUEIRO
};

typedef struct {
    char *nome;
    enum tipoDeBarco tipo;
    float vel_max;
    int tamanho;
} Barco;

bool comparaBarcos(Barco barco1, Barco barco2);

#endif
```

> De imediato você já deve ter notado o uso das diretivas de pré-processador. Aqui, elas estão servindo o propósito de _header guard_ que citei antes. Basicamente, o fato de o `#define BARCOS_H` estar dentro do `#ifndef BARCOS_H` garante que a definição de `BARCOS_H` irá acontecer apenas uma vez, mesmo que nós dermos `#include` neste cabeçalho em múltiplos arquivos C. O valor de `BARCOS_H` neste contexto é o conteúdo do header inteiro, então não colocar o `header guard` poderia causar erros de "múltiplas definições".

Com este cabeçalho escrito, nós podemos no arquivo `main.c` simplesmente escrever a linha `#include "barcos.h"` para ter acesso tanto ao enum quanto ao tipo `Barco` e à função `comparaBarcos`.

Contudo, a função ainda não está definida, então chamar ela é impossível por enquanto. Para defini-la, vamos criar um novo arquivo: o `comparador.c`.

``` C
#include <stdbool.h>
#include "barcos.h"

int avaliaBarco(Barco barco);

// retorna true se barco1 for mais deslumbrante do que barco2
bool comparaBarcos(Barco barco1, Barco barco2) {
    return avaliaBarco(barco1) > avaliaBarco(barco2);
}

// retorna um número dizendo o quão deslumbrante um barco é
int avaliaBarco(Barco barco) {
    if(barco.tipo == VELEIRO) {
        return 100 + barco.tamanho;
    } else if(barco.tipo == CANOA) {
        return 200;
    } else if(barco.tipo == IATE) {
        return 50 + 2 * barco.tamanho;
    } else if(barco.tipo == PESQUEIRO) {
        return 100000;
    }
}
```

Como você pode ver, neste arquivo nós não apenas definimos a função `comparaBarcos`, como também fizemos uso de uma função auxiliar `avaliaBarco`, que - apesar de não estar no header e não ficar disponível para demais arquivos - pode ser usada em seu arquivo de origem tranquilamente.

Feito isso, podemos ir para o `main.c` e concluir o ciclo da vida, fazendo uso de tudo que foi declarado em nosso cabeçalho:

``` C
#include <stdio.h>
#include <stdbool.h>
#include "barcos.h"

void main() {
    Barco pesqueiroLendario = {"A lenda", PESQUEIRO, 80.0f, 40};
    Barco iateBucha = {"Barril", IATE, 150.0f, 60};
    bool pesqueiroMassacrou = comparaBarcos(pesqueiroLendario, iateBucha);

    if(pesqueiroMassacrou) {
        printf("O pesqueiro é mais deslumbrante, quem imaginaria?");
    } else {
        printf("Algo deve estar errado, o iate não tinha chances contra o pesqueiro...");
    }
}
```

> Como este programa possui múltiplos arquivos, para compilar o programa você precisa listar todos os `.c` separadamente ao rodar o `gcc`. Ou seja, rode `gcc main.c comparador.c -o programa.out`, ou simplesmente `gcc *.c -o programa.out`

Rodando este código, você verá nitidamente em seu terminal que o barco pesqueiro sola tudo, vamboraaaaa!!! Enfim, é assim que se utiliza um cabeçalho, recapitulando:

1. Você cria um `.h` com a declaração do que você quiser compartilhar com outros arquivos
2. Você define os componentes do header em um ou mais arquivos `.c`
3. Você importa o header nos arquivos necessários com `#include "nome_do_header.h"`

## Conclusão

Este capítulo foi um tanto quanto denso, tal qual as águas salgadas do mar - Har Har Har har....... Então se você se sentiu um pouco perdido, não tenha vergonha de pedir ajuda ao profissional do C mais próximo de você! (rimou)

O único jeito de se acostumar com todos estes conceitos e sintaxes é praticando, então coloque a mão neste tecladão e saia digitando com seu coração (não literalmente, isso machucaria bastante).

Dito isso, daqui onde estamos já dá para avistar um belo arquipélago no horizonte; um conjunto de ilhas o qual iremos explorar nos próximos capítulos. Respire fundo e mantenha a cabeça alta, pois a partir de agora as coisas ficam ainda mais interessantes! Até lá :^D
