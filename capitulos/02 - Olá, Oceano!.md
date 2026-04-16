# Table of Contents

1.  [Capítulo 2 - Olá, Oceano!](#org0f7efe7)
2.  [Olá, Mundo!](#org1f90453)
3.  [Variáveis](#orgf21606d)
    1.  [Declaração](#orgb0203b6)
    2.  [Tipos](#org9570bda)
        1.  [Char](#org61562e9)
        2.  [Ints](#orgd9b3440)
        3.  [Floats](#org43ffad5)
        4.  [Qualificadores](#org7c51a87)
        5.  [Bools](#org728e322)
        6.  [Enums](#org9802952)
4.  [Condicionais](#orgfd4c8b1)
    1.  [If](#org28f6314)
    2.  [Else](#org3decb62)
    3.  [Expressões idiomáticas com `if` e `else`](#org6a5ccd4)
        1.  [`If`, `else if` e `else`](#org082f1c5)
        2.  [Escadas](#orga7f623c)
        3.  [Aninhamento](#orgca11a06)
    4.  [Switch](#org7d5e087)
    5.  [Ternário](#orgb362701)
    6.  [Sobre o uso de GOTO](#org480c35f)
5.  [Laços](#orgeec025f)
    1.  [While](#org01591c0)
    2.  [For](#org27cdf32)
6.  [Exercício de Fixação](#org1e9983e)
7.  [Rodapés](#orge450ba8)


<a id="org0f7efe7"></a>

# Capítulo 2 - Olá, Oceano!

Pelas barbas de Netuno, finalmente vamos programar!


<a id="org1f90453"></a>

## Olá, Mundo!

Somos supersticiosos, então, para seguir, temos que fazer você compilar e rodar o seguinte encantamento:

``` C
#include <stdio.h>

int main(){
    printf("Olá, Mundo!\n");
    return 0;
}
```

Salve ele em um lugar onde você vai lembrar!

E para compilar e rodar o programa, você deve executar o seguinte comando na pasta onde você o salvou:

``` sh
gcc -o hello-world hello-world.c;
./hello-world
```

Se tudo correu bem, você deve ter visto na linha de comando a frase `Olá, Mundo!`.

Por mais que não seja muito interessante, é de suma importância você ter feito isso. Não conhecemos ninguém de SI que esteja vivo e não tenha escrito esse singelo programa. Preferimos não descobrir o que acontece caso contrário.

Vamos dissecar melhor ele ao longo dos próximos capítulos, mas entenda que:

-   O `#include <stdio.h>` pede para o pré-processador (assunto do capítulo 03) acrescentar a definição do `printf()` no nosso programa;
-   O `printf()` é uma função (conceito que também vamos abordar no próximo capítulo) que imprime a frase na tela. Ela toma caracteres de controle para modificar a impressão. Vamos falar dela melhor no futuro;
-   Todo programa em C precisa, necessariamente, da função `main()`. Ela tem essa carinha ali (quase) sempre. Ela é o ponto de entrada de todo e qualquer programa;<sup><a id="fnr.1" class="footref" href="#fn.1" role="doc-backlink">1</a></sup>
-   Tudo dando certo com o nosso programa, ele avisa para o sistema operacional que ele acabou, e não só isso, ele devolve para o SO o valor 0, que significa "tudo correu bem".

E isso foi a forma curta de falarmos do programa!

Sugiro você tentar remover coisas dele e ver o que continua funcionando ou não. Alguns pontos de interesse:

-   E se você tirar o `\n` no fim da frase?
-   E se tirarmos o `#include<stdio.h>`?
-   O que acontece se mudarmos o valor do `return` para alguma coisa além de 0?
-   Que tal trocar a frase?
-   E se deixarmos o programa todo em uma linha só??

Brinque um pouco, mas temos ainda bastante coisa para ver!

<a id="orgf21606d"></a>

## Variáveis

De nada servem programas se eles não conseguirem lembrar de coisas para nós.

Para que o programa lembre de coisas, temos vários mecanismos. Aqui, vamos ver o mais simples deles: as variáveis. Variáveis são "caixinhas" onde podemos guardar valores, como veremos logo a seguir.

Para usarmos variáveis, elas têm que ser declaradas.

<a id="orgb0203b6"></a>

### Declaração

Todas as declarações, via de regra, tem a mesma cara: `tipo nome_da_variavel = valor;`.<sup><a id="fnr.2" class="footref" href="#fn.2" role="doc-backlink">2</a></sup>

A coisa importante é que as variáveis tem um nome, do lado esquerdo do `=`, que será usado para fazer referência à ela, além do tamanho necessário para guardar os dados, determinado pelo `tipo`. O valor de fato que será guardado fica do lado direito do `=`. Lembra de como a memória é uma estante? O nome nada mais é que uma caixa de papelão que colocamos lá e anotamos com caneta. É mais fácil lembrar do nome do que o código do endereço.

Estendendo nossa analogia de estante, o que colocamos dentro dessa caixa é o `valor`. Podemos declarar também da forma `tipo nome_da_variavel;`, sem o `valor`, mas isso não é exatamente bom, já que vamos ter uma caixa, mas não sabemos o que tem dentro dela. E já que não queremos descobrir o que há nela, colocaremos sempre um valor condizente.

Por fim, para o compilador separar o tamanho correto na estante para caber nossa caixa, avisamos através do `tipo`. E já que o sistema de tipos do C é fundamental para várias linguagens que vieram depois, vamos tratar um pouco deles agora.

<a id="org9570bda"></a>

## Tipos

Para fins didáticos, os tipos são relativamente poucos. Caso você faça muita questão, mas muita mesmo, leia os anexos D e E do [rascunho da especificação ISO para Linguagem C](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n3096.pdf), a Seção 6.7 também. Ótimo se você quiser perder tempo, entender um *bug* extremamente obscuro ou tiver problemas para dormir.

Agora que você matou essa curiosidade mórbida, podemos seguir.

<a id="org61562e9"></a>

### Char

São caracteres. No C, não há uma forma nativa de produzir cadeias de caracteres como outras linguagens de programação, como Python, Java e mais.

Isso é uma forma complicada de dizer que frases inteiras não são nativas em C, mas apenas as letras individuais.

``` C
char letra_A = "A";
char letra_a = "a";

char *frase = "Uma frase cumprida";
```

Veja que para criar uma frase usamos a forma `char *`. Lemos isso como "um ponteiro para caracteres", ou ainda "uma cadeia de caracteres".

Vamos ver melhor o que isso significa na parte de ponteiros, mas isso é para você não estranhar certos exemplos.

<a id="orgd9b3440"></a>

### Ints

São os valores inteiros. Eles podem ser positivos ou negativos, a depender do que você pedir. Em matematiquês, isso significa valores que vivem em Z.

``` C
int inteiro = 0; // Inicialize com algum valor para você não se chatear no futuro
unsigned int natural = 0; // Ao não precisarmos do sinal, ficamos com o dobro de valores representáveis!
signed int numero = 0; // Ele é equivalente ao int sem nada mesmo
```

Acredito que esse é o tipo mais comum que você vai usar, muito pela sua imensa utilidade.

<a id="org43ffad5"></a>

### Floats

Chamados de *ponto flutuante*, eles são os números no conjunto R da matemática. Eles também são chamados de *reais*.

Entretanto, temos uma questão: computadores são, nada mais e nada menos, que ábacos rápidos e complicados. Então, é da natureza deles serem limitados. Sendo assim, a precisão de contas com vírgula é limitada.

Não vamos tratar das minúscias do comportamento, já que eles são super complicados. Mas entenda que temos limites para a precisão e podemos pedir para o computador aumentar a precisão.

``` C
float real = 3.1415;

double duplamente_preciso = 3.14159265359;
double notacao_cientifica = 2e-10;
```

Temos várias formas de declarar reais, mas essas são bem comuns, a com o ponto como separador (já que a origem é o inglês) e a notação científica.

O melhor uso, para projetos de jogos no geral, é saber com precisão o local de um personagem na tela, um inimigo, um projétil e por aí vai.

<a id="org7c51a87"></a>

### Qualificadores

Podemos modificar certos comportamentos do tamanho da variável que pedimos para o compilador separar na memória.

``` C
short int curto = 0;
long int comprido = 0;
long long int bem_comprido = 0;
long long unsigned int o_mais_comprido = 0;
```

Essas palavras antes de `int` são os qualificadores de tamanho. Eles mudam, bem, o tamanho da memória que o compilador separa para a gente e como certos dados são interpretados. Um número com modificador `short` ocupa menos espaço na memória, mas tem um limite inferior e superior muito mais apertado - e o oposto vale para números `long` ou `long long`.

Temos também outra família de qualificadores, os de comportamento:

``` C
const int constante = 0; // O valor não pode ser modificado
volatile int volatil = 0; // Avisamos que o valor pode mudar fora do programa
extern int externo = 0; // Um símbolo externo, para o compilador não se preocupar
// e mais...
```

Desses, memorize apenas o `const`, já que é o mais comum.

1.  Um detalhe da linguagem para `char`

    A especificação do C, entre algumas garantias de implementação, é sobre o tamanho do `char`.
    
    Entretanto, há ainda a forma do `unsigned char`, que é sempre exatamente um *byte* para a sua arquitetura.
    
    Então, se você precisar, em geral, de exatamente 8 *bits* para guardar algo, esse é o seu cara.<sup><a id="fnr.4" class="footref" href="#fn.4" role="doc-backlink">4</a></sup>
    
    Não se preocupe muito de lembrar disso, mas é para não te causar estranhamento quando você ver alguém declarando um `unsigned char` e o compilador não reclamar.


<a id="org728e322"></a>

### Bools

Lembre-se da nossa aulinha de lógica booleana no capítulo 00. No caso, C23 tem as palavras chave:

``` C
bool falso = false;
bool verdade = true;
```

Antes, você tinha que chamar um cabeçalho para ter essa funcionalidade ou chamar o confuso e feio tipo `_Bool`.

Porém, a linguagem C ainda mantém um comportamento (e lembre-se da álgebra booleana!):

-   Se algo tem valor 0, é falso;
-   Qualquer coisa que não 0 é verdadeiro. Valores reais e negativos são verdadeiros.

Então, você vai ver (e provavelmente escrever) código que não use apenas o tipo `bool` para ver se algo é verdadeiro ou falso.


<a id="org9802952"></a>

### Enums

Vamos passar por outras formas de listar valores, mas essa aqui é bem legal. Se você precisa de uma lista de valores que são tematicamente parecidos, as enumerações (ou *enums* para os próximos) te ajudam.

Por exemplo, mantendo o nosso tema nautico, você precisa da listagem das oito direções cardinais, para ajudar na navegação. Um exemplo, começando do norte e seguindo no sentido horário:

``` C
enum Direcoes = {
    NORTE,
    NORDESTE,
    LESTE,
    SUDESTE,
    SUL,
    SUDOESTE,
    OESTE,
    NOROESTE
};
```

O compilador é espertinho, então ele atribui os valores para os nomes em ordem, com `NORTE = 0`, `NORDESTE = 1` e assim por diante.

Mas, e se quisermos dar o ângulo? Podemos ter um joguinho naval que precisa mostrar nosso barco indo para a direção e o modelo do barco depende desse ângulo!

Podemos refazer asism então:

``` C
enum Direcoes = {
    NORTE = 0,
    NORDESTE = 45,
    LESTE = 90,
    SUDESTE = 135,
    SUL = 180,
    SUDOESTE = 225,
    OESTE = 270,
    NOROESTE = 315
};
```

Agora, temos essa atribuição.

E para usarmos, fazemos o seguinte:

``` C
enum Direcoes angulo = SUDESTE;
```

Agora, o valor dentro de `angulo` é `135`. Mas é meio feio ter que usar ele sempre desse jeito, então temos uam forma de criar tipos em C: os `typedefs`. Vamos ver isso mais a fundo no próximo capítulo, já que ganhamos mais flexibilidade lá, mas as declarações são sempre assim:

``` C
// Convertendo o nosso exemplo anterior:
typedef enum {
    NORTE = 0,
    NORDESTE = 45,
    LESTE = 90,
    SUDESTE = 135,
    SUL = 180,
    SUDOESTE = 225,
    OESTE = 270,
    NOROESTE = 315
} Direcoes;

// E a declaração e atribuição anteriores:
Direcoes angulo = SUDESTE;
```

É meio estranho no começo, mas você, basicamente, diz para o compilador `typedef` ("vou te ensinar um tipo") `tipo` ("que tem esse tipo") `{...}` ("e tem essa cara aqui") e `nome` ("e se chama `nome`").

Por mais que seja meio estranho, ainda é melhor que dar valores mágicos para as coisas, e também é mais fácil de lembrar. Especialmente com um próximo contructo.

<a id="orgfd4c8b1"></a>

## Condicionais

Tudo bem só sabermos o básico do básico até agora. Essa informação toda até agora é legal para partes bem lineares do seu programa, como a sequência para zarparmos de um porto.

Mas, e se, na grande chance de ocorrer um problema, nosso programa precisar responder de modo mais inteligente?

As condicionais nos salvam!

Nós declaramos condições na forma de algebra booleana (para qual o C tem uma simbologia própria) e, de acordo com o resultado, nosso programa faz algo diferente. Lembre-se que expressões booleanas podem ter apenas VERDADEIRO ou FALSO como resultado, então podemos ter duas construções interessantes para isso: as árvores e as escadas. Vamos lá!

<a id="org28f6314"></a>

### If

Por si só, o `if` nos dá muita capacidade de agir. Seguindo com o exemplo de sairmos de um porto:

``` C
if(ancora_abaixada == true) levantar_ancora();
```

Então, se a âncora ainda está abaixada, precisamos realizar um procedimento de levantamento dela.

Podemos também encadear comportamentos:

``` C
if(tudo_pronto_para_viagem == true){
    levantar_ancora();
    icar_velas();
    tracar_rota();
    zarpar();
}
```

Nesse caso, devemos colocar as chaves para que o programa faça tudo isso se o valor `tudo_pronto_para_vaigem` for igual a `true`.

No caso, a comparação booleana em C é `==`. O porquê disso é pelo `=` já ser a atribuição de um valor à uma variável.

Também é comum você encurtar a expressão da seguinte forma:

``` C
if(ancora_abaixada) levantar_ancora(); // Equivalente ao nosso exemplo ale de cima
```

E, caso você queira aportar o seu navio, temos a seguinte possibilidade:

``` C
if(!ancora_abaixada) baixar_ancora();
```

Ou seja, estamos invertendo o valor de `ancora_abaixada`. Isso é o nosso NOT() da parte de álgebra booleana.
O exemplo se traduz para "se a âncora não estiver abaixada, faça `baixar_ancora()`".

Não vamos nos extender muito nos comportamentos booleanos da linguagem, já que são simples e sua complexidade surge de como combinamos eles.

A título de exemplo:

``` C
if(capitao_a_bordo && timoneiro_a_bordo && ancora_levantada) zarpar();
```

O `&&` siginifica o AND(). Da mesma forma, o `||` (fica ali perto da barra de espaço, do lado esquerdo, no teclado BR) significa OR(). Por exemplo:

``` C
if(problema_no_casco || problema_na_ancora || problema_com_tripulacao) abortar_viagem();
```

Podemos compor eles para termos o comportamento mais complexo, assim como na álgebra regular.

<a id="org3decb62"></a>

### Else

O Garfunkel para o nosso Simon do `if`. Se você não entendeu, não importa muito.

Com essa construção, podemos expandir nosso repertório de comportamentos. Já que se você percebeu um problema no uso de apenas `if`: não estamos usando metade do comportamento binário da lógica booleana. Que desperdício!

Usamos o `else` para fazer o complemento de algum if. Logo, se a expressão dentro do `if` resultar em `false`, o código dentro do `else` é executado no lugar. Reciclando um dos nossos exemplos:

``` C
if(tudo_pronto_para_zarpar){
    zarpar();
} else {
    preparar_para_zarpar();
}
```

Ou seja, se estiver tudo pronto, podemos zarpar, **mas caso contrário**, precisamos `preparar_para_zarpar()`.

Tal como o `if`, o comportamento fica ali dentro das chaves. E lembre-se que eles são mutuamente excludentes (por isso que não precisamos de um `else(!tudo_pronto_para_zarpar)`), então é bem econômico mesmo.

Um exemplo comum de algo que é mutuamente excludente é se um número é par ou ímpar, se algo está ligado ou não, se há conexão com a internet ou não e por aí vai.

<a id="org6a5ccd4"></a>

### Expressões idiomáticas com `if` e `else`

Temos três usos bem comuns dessas contruções, mais abaixo.

Pense que, se você quer navegar bem, você precisa reconhecer ventos e ondas. Esse aqui é o equivalente, reconhecer o que esses padrões significam para você melhor interpretar o que quem programou queria dizer.

<a id="org082f1c5"></a>

### `If`, `else if` e `else`

Pense que você tem uma série de decisões para colocar no seu programa, como se você vai cuidar do cardápio de um dia no navio. Esse cardápio varia segundo o dia da semana.

Podemos escrever então:

``` C
typedef enum {
    DOMINGO,
    SEGUNDA,
    TERCA,
    QUARTA,
    QUINTA,
    SEXTA,
    SABADO
} dias_da_semana;

dia_da_semana hoje = dia_de_hoje();

if(hoje == DOMINGO){
    servir_frango();
} else if(hoje == SEGUNDA) {
    servir_sobras_fim_de_semana();
} else if(hoje == TERCA) {
    servir_macarrao();
} else if(hoje == QUARTA) {
    servir_feijoada();
} else if(hoje == QUINTA) {
    servir_sushi();
} else if(hoje == SEXTA) {
    servir_pizza();
} else { // Se for SÁBADO
    servir_feijoada();
};
```

A vantagem dessa forma é que, caso o dia já seja domingo, ele ignora todo o resto, tornando seu programa mais previsível e mais rápido.

Até mesmo se for sábado, o programa ainda é relativamente rápido, já que ele não tenta servir todos os cardápios de uma vez.

Já já falamos de uma outra opção de como escrever um código equivalente bem rápido também, mas se segure!

A outra grande utilidade desse tipo de construção é como você pode dar *intervalos* para as condições.
Por exemplo:

``` C
if(idade_passageiro < 0){
    printf("Impossível!\n");
} else if(idade_passageiro > 0 && idade_passageiro < 4){
    oferecer_carrinho_de_bebe();
} else if(idade_passageiro >= 4 && idade_passageiro < 12{
    oferecer_servico_de_recreacao();
} else if(idade_passageiro >= 12 && < 18){
    oferecer_pacote_radical();
} else if(idade_passageiro >= 18 && < 65){
    oferecer_pacote_open_bar();
} else { // Equivalente idade_passageiro >= 65
    oferecer_pacote_melhor_idade();
}
```

Nesse caso, é legal por serem categorias mutuamente excludentes, mas com intervalos relativamente grandes entre si.

<a id="orga7f623c"></a>

### Escadas

Voltando ao exemplo de comida, digamos que você tem que enviar para a cozinha os pedidos dos clientes. A pessoa pode pedir um prato principal, uma bebida e uma sobremesa. Nesse caso, não se ligue muito no "e", já que ele está com o significado coloquial da coisa.

``` C
if(tem_bebida) trazer_bebida();
if(tem_prato) trazer_prato_principal();
if(tem_sobremesa) trazer_sobremesa();
```

Isso é chamado de "escada", com cada `if` sendo um degrau. A diferença dela para o caso anterior é que o programa avalia *cada um* dos `ifs`. Isso acontece porque, para o nosso exemplo, uma pessoa pode querer apenas um prato principal e mais nada, ela pode querer tudo ou, ainda, só uma bebida e uma sobremesa (café com bolo?).

Nosso programa é perfeitamente capaz de tratar desses casos.

Mas, novamente, a parte mais poderosa, é que ele pode avaliar intervalos também. Por exemplo:

``` C
if(numero % 2) numero_impar(); // A conta é se o resto da divisão por 2 é 0 ou não. Ou seja, se ele é ímpar
if(numero < 1000) fazer_algo();
if(numero >= 100) fazer_tambem_outra_coisa();
```

Se, por exemplo, o número for 111, que é ímpar e menor que 1000 e maior ou igual a 100, nosso programa faz tudo.

Isso tem certas vantagens e desvantagens comparado ao ao uso de vários `||` e `&&` dentro de só um `if`, entre elas, condições separáveis de acordo com uma característica. Por exemplo, você não quer escrever um caso para tudo e outro para tudo, mas par.<sup><a id="fnr.5" class="footref" href="#fn.5" role="doc-backlink">5</a></sup>

<a id="orgca11a06"></a>

### Aninhamento

Podemos colocar `ifs` um dentro do outro, que é interessante para dar comportamentos que dependem de um encadeamento de condições.

Por exemplo:

``` C
if(todos_dados_prontos){    
    dados_preprocessados = realizar_preprocessamento();
    if(dados_preprocessados){
        calcular_resultado_final();
    }    
}
```

Nesse caso, nós separamos dois passos computacionalmente caros em etapas, para agilizar o programa.

Isso pode ser chamado de "preguiçoso" (é o termo correto mesmo!), o que nos ajuda a separar, no exemplo, o pré-processamento de dados. Só faz sentido essa etapa acontecer se todos os dados estiverem prontos.

E, no caso, salvamos o retorno da etapa de pré-processamento em uma variável (vamos fingir que foi declarada previamente), e pelo que esses dados pré-processados nos dizer, calculamos o resultado final, que também é bem caro.

Uma operação computacionalmente cara é, de modo simples, tudo o que o computador demora para fazer. A nossa única moeda de fato é tempo.

Um exemplo de uma operação cara é a calcular o estado completo de um mundo em um jogo. Mais especificamente, se esse mundo tem física complexa, um monte de personagens e mais. Então pense que o sistema de exibição do jogo (os gráficos, a renderização), pode aguardar até o sistema de física terminar seus cálculos. Na hora que a física estiver pronta, podemos desenhar na tela.

Isso faz o sistema de renderização não ficar brigando com o sistema de física pela CPU.

Vamos ver aqui na frente como aninhamentos também podem ser problemáticos.

<a id="org7d5e087"></a>

### Switch

Lembre-se da nossa escada de `ifs`. Se nós temos uma escada que usa enumerações ou tem um número limitado e discreto (ao invés de contínuo) de estados, podemos usar esse cara:

``` C
switch(variavel_discreta){
    case VALOR_A:
        faz_algo();
        break;
    case VALOR_B:
        faz_outra_coisa();
        break;
    default:
        caso_padrao();
        break; // Ele é opcional, mas recomendado pelo estilo
}
```

Viu só como fica mais organizadinho? Inclusive, temos o `else` ali, mascarado como o `default`.

Veja duas coisas importantes:

-   O valor para cada caso é, obrigatoriamente, discreto. Ou seja, coisas como 'A' ou "123123" valem, mas "Frase grande", funcao<sub>com</sub><sub>retorno</sub>() ou "3.14" não;
-   Temos esses `breaks` entre cada caso para fazer ele se comportar que nem uma escada de `else if`. Se você quiser que seja que nem uma escada de `if`, pode omitir o `break`.

Um exemplo comum:

``` C
switch(etapa_procedimento_saida){
    case PAPELADA_ENVIADA:
        levantar_rampas();
    case RAMPAS_LEVANTADAS:
        levantar_ancora();
    case ANCORA_LEVANTADA:
        ligar_motores();
    case MOTORES_LIGADOS:
        zarpar();
        break;
    default:
        mandar_papelada();
}
```

Nesse caso, ele pula para a etapa e começa a executar de lá. Se eles já mandaram a papelada para a aduana, o procedimento todo é executado na ordem.
Se não for nenhum desses casos, o padrão é mandar a papelada, que é o primeiro passo.

Esse comportamento do `switch` atravessar cada caso (se não houver o `break`) é chamado de *fall through*.

<a id="orgb362701"></a>

### Ternário

Já que o `if` é tão comum, temos uma forma curta para ele:

``` C
(ancora_levantada) ? zarpar() : levantar_ancora();
```

Nós lemos isso como "A âncora está levantada? Se sim, zarpar; se não, levantar a âncora".

Não só ele é uma versão mais compacta de um `if`, mas ele também pode servir como valor para a atribuição para uma variável:

``` C
int capacidade;
capacidade = (navio_de_carga) ? numero_conteiners : numero_passageiros 
```

Ou seja, se o navio for de carga, a capacidade dele é cotada em contêneires, e se for de passageiros, é pelo número de passageiros.

<a id="org480c35f"></a>

### Sobre o uso de GOTO

Há uma certa controvérsia sobre o constructo `goto` ("vá para") desde o famoso Djikstra ter escrito o breve artigo [Go To Statement Considered Harmful](https://homepages.cwi.nl/~storm/teaching/reader/Dijkstra68.pdf) ("*Go to* considerado danoso"), em 1968. Desde então, muitas linguagens evitam a inclusão do `goto`.

Leia o artigo, ele tem uma página e meia, sendo muito breve. Mas o ponto principal é que essa palavra-chave tende a gerar saltos complicados de lógica, ao invés das construções mais comportadas, como `if`, `switch` e afins.

Entretanto, nós temos que discordar sobre seu uso *adequado* em C. Sempre que possível, é importante usar as outras construções, já que sua lógica é bem localizada (e localizável). Porém, há certos tipos de problemas que o `goto` causa o controle mais simples de fluxo, melhorando a legibilidade do programa, e por sua vez, reduzindo a chance de *bugs* em programas complexos.

Não precisa concordar conosco para estarmos certos. Veja o *kernel* do Linux, cheio de `goto`, especialmente nas partes que precisam tratar erros relacionados a pegar recursos compartilhados do sistema.

Um pequeno exemplo:

``` C
drive_disco = pegar_controle_disco();
if(drive_disco == problema_drive_disco) goto problema_disco;

fazer_operacao_disco();

devolver_controle_disco();

return 0;

problema_disco:
return 1;
```

Nesse caso, se o nosso programa tentar pegar controle do disco, mas falhar, ele precisa tratar esse erro, e no caso, encerrando o programa com um código de erro.

Se o programa conseguir pegar o controle correto do disco, ele faz a operação que precisa, libera o acesso (pois ele estava com o controle do disco) e termina o programa sem erros.

Os membros do comitê da linguagem recomendam tratamento de erros dessa forma.<sup><a id="fnr.6" class="footref" href="#fn.6" role="doc-backlink">6</a></sup> E sobre o *kernel*, temos esse vídeo que ajuda a visualizar as decisões nessa peça de programa: [Every goto in the Linux kernel / Just another day on the linux-kernel mailing list](https://www.youtube.com/watch?v=v1Mfirg2-Z8).

<a id="orgeec025f"></a>

## Laços

A penúltima construção básica em qualquer linguagem de programação é realizar um conjunto de instruções repetidamente. Ela também é chamada de *loop*.

Podemos pedir para o computador realizar algo um número de vezes ou enquanto uma condição for verdade.

Ambas as formas a seguir são equivalentes, mas da mesma forma que você tem sinônimos na língua portuguesa, um é melhor para uma situação e o outro, para outra, a partir do significado.

<a id="org01591c0"></a>

### While

Traduzido livremente para "enquanto". Nós tendemos a usar ele para algo acontecer *enquanto* um critério é verdade. Por exemplo:

``` C
while(!chegamos_destino){
    navegue();
    chegamos_destino = (chegamos()) ? true : false;
}
```

No caso, continuamos navegando enquanto a condição (*não* chegamos no destino) é verdadeira.

Note que há uma função que verifica para nós se chegamos. Se sim, a variável `chegamos_destino` fica verdadeira e vamos sair do *loop*.

Caso haja um passo inicial de preparação, mas ao mesmo tempo ele deverá ser refeito, podemos escrever assim:

``` C
do {
    sirva_refeicao();
    entretenha_visitantes();
} while(!chegamos_destino);
```

Nesse caso, enquanto não chegamos no destino, comida deve ser servida e os hóspedes devem ser entretidos durante o cruzeiro.

A graça dessa forma é que você não precisa ter um caso especial para o primeiro dia e outro, dentro do laço, para todos os dias subsequentes.

Também pode acontecer de você precisar verificar algo ou fazer uma série de operações sempre antes de dar continuidade ao *loop*.

<a id="org27cdf32"></a>

### For

Usado para repetir uma ação um número X de vezes, com X sendo um número conhecido. Por exemplo:

``` C
for(int i = 0; i < total_hospedes; i++){
    verifique_cadastro(i);
    de_boas_vindas(i);
    indique_quarto(i);
}
```

Os loops `for` possuem dentro de seus parênteses três partes, separadas por `;`. Essas partes são:

1. A inicialização de um "iterador", um número que vai mudando a cada loop. Geralmente chamamos o iterador de `i`. No nosso caso, temos `ìnt i = 0`.
2. Uma condição para a parada do loop. Quando essa condição deixar de ser verdadeira, nosso loop para. No nosso caso, temos a condição `i < total_hospedes`.
3. Uma modificação na variável de iteração, para que não fiquemos presos em um loop infinito. No nosso caso, fazemos `i++`, que é o mesmo que `i = i + 1`.

Sendo assim, toda a vez que o nosso laço terminar de realizar todas as operações, ele aumenta em um o `i` e verifica a sentença ali do meio. Enquanto não é falsa a expressão, o laço é executado na íntegra.

<a id="org1e9983e"></a>

## Exercício de Fixação

Não, ele não é opcional!

Agora, vamos tratar de um clássico: o *fizzbuzz*. Eu adoro esse programa pela sua simplicidade e variedade.

Sua definição é:

-   Temos os números de 0 até N como entrada;
-   Ele imprime na linha de comando os números de 0 até N. Temos apenas um número por linha;
-   Se o número for múltiplo de 3, ao invés do número impresso, deve imprimir a palavra "fizz";
-   Se o número for múltiplo de 5, ao invés do número impresso, deve imprimir a palavra "buzz";
-   Se o número for múltiplo de 3 e de 5, a impressão na tela deve ser "fizzbuzz";
-   Se o número não for múltiplo de nenhum desses, imprimimos o número de fato.

Um exemplo para a saída do 15:

```
0
1
2
fizz // 3
4
buzz // 5
fizz // 6
7
8
fizz // 9
buzz // 10
11
fizz // 12
13
14
fizzbuzz // 15
```

Vou te dar já um adianto aqui:

``` C
#include <stdio.h>

int main(){
    int n;
    
    // Para imprimir coisas na tela:
    printf("fizz\n");
    printf("buzz\n");
    printf("%i\n", n); // Substitui o %i pelo valor atual de n
    
    // Seu código entra aqui
    
    return 0;
}
```

Tente, vai ser legal!

Se precisar muito, peça ajuda! Mas, de modo geral, você vai precisar de condicionais e laços.

Boa sorte.

<a id="orge450ba8"></a>

## Rodapés

<sup><a id="fn.1" href="#fnr.1">1</a></sup> Isso, tecnicamente, não é uma verdade. No caso, a função `main()` só é obrigatória em programas que rodam em um sistema operacional. Dois exemplos que não precisamos de uma `main()` por não haver um SO: o *kernel* de Linux e sistemas embarcados.

<sup><a id="fn.2" href="#fnr.2">2</a></sup> Se quisermos ser mais chatos ainda, o nome "correto" do símbolo<sup><a id="fnr.3" class="footref" href="#fn.3" role="doc-backlink">3</a></sup> `nome_da_variavel` é `lvalue` e do `valor` é `rvalue`. Isso é do mnemônico inglês *left value* e *right value*. "Valor esquerdo" e "valor direito". Sim, fascinante. Explique isso para a sua mãe e ela ficará impressionada.

<sup><a id="fn.3" href="#fnr.3">3</a></sup> Essa é uma forma super formal de chamarmos "os trecos com valor sintático" que o compilador lê. Não importa muito agora como o compilador faz isso, mas entenda que coisas como `int`, `;`, `{}`, `um_nome_bem_comprido_de_variavel`, `12312313` e `123.123123e2` são exemplos de símbolos.

<sup><a id="fn.4" href="#fnr.4">4</a></sup> Nem toda arquitetura usa oito *bits* para um *byte*. O `unsigned char` te garante um *byte* exato para a sua arquitetura. Mas, por exemplo, a série PDP de computadores usa 9 *bits* para formar um *byte*, tendo seu tamanho natural 36 *bits*, ou seja, 4 *bytes*, assim como os computadores de 32 *bits* também tem 4 *bytes*, mas de 8 *bits* cada. Isso é um detalhe, não se preocupe muito.

<sup><a id="fn.5" href="#fnr.5">5</a></sup> Tem também certas otimizações de casos de falha rápida, mas não vamos falar disso agora, já que é um tipo de otimização que vale ser feita só se você realmente precisa de cada ciclo. Também, esse curso é só introdutório, então não vamos nem mesmo conseguir te dar as ferramentas de análise necessárias para você fazer essa análise.

<sup><a id="fn.6" href="#fnr.6">6</a></sup> A única forma ideal para tratar erros é se a linguagem tivesse a própria forma de tratar erros, como exceções e mais. Mas até mesmo linguagens como Python tendem a fazer um rocambole com `try` / `catch` complicados e cumpridos. Acredtie, você vai usar até pouco o `goto`, e quando precisar, vai ser bem claro e fácil.
