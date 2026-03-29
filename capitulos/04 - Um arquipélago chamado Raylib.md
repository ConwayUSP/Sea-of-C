
# Table of Contents

1.  [Preparações para Explorar](#org82816fe)
2.  [Arquitetura da Raylib](#orged83843)
    1.  [Um pouco sobre a divisão](#org42a3c62)
3.  [Conhecendo a API](#org828384a)
    1.  [De volta ao primeiro exemplo](#org2b99714)
        1.  [Inicialização (e finalização)](#org32bfcff)
        2.  [Mantendo a janela aberta](#orgeba1340)
        3.  [Fazendo algo (um pouco) interessante](#org5997d59)
    2.  [Mais um exemplo simples](#org7221621)
        1.  [`SetTargetFPS()`](#org951e839)
        2.  [Desenhando e movendo a bola](#orge491d1d)
    3.  [Finalizando a seção](#org4c4f6e5)


<a id="org82816fe"></a>

# Preparações para Explorar

Olá, grumete!

Esperamos que você já tenha algum jogo de cintura com essa linguagem simples, porém muito capaz!

Porém, temos algumas coisinhas que nós, marinheiros mais acostumados, temos para dar de dica:

-   Daqui pra frente, tenha em mãos um computador ou *laptop*. Não acreditamos que faça muita diferença a arquitetura do processador, mas é importante ter um sistema operacional como Linux (nosso predileto!), Windows ou MacOS. Caso você não tenha posse de um desses, lembre-se da pró-aluno que podemos usar! E não só isso: ler e se planejar é metade do trabalho! Enquanto você não está com o computador, planeje como você quer fazer algo e leia um pouco sobre se a solução faz sentido. Anote, desenhe e, na hora que você tiver acesso ao computador, as brigas serão (em sua maioria) com o compilador, e não com o seu cérebro!
-   Antes de escrever bem, você precisa conseguir ler bem. Mas isso não te permite "só começar a escrever quanto estiver tudo certo". Leia os arquivos da biblioteca, que é muito bem escrita, e você já terá uma boa ideia do que é um bom programa de C. Outros exemplos, se você usa Linux, são o próprio *kernel*, projetos como cURL, a sua pasta mesmo de `includes` que você tem no seu SO e mais. Não tenha medo, você pode não entender nada, mas eu prometo que alguém no Stack Overflow já teve a mesma pergunta do porque diabos alguém escreveu algo da forma que escreveu. E aí, nós sugerimos você usar expressões semelhantes no seu programa!

Vamos explorar juntos!

Vá até o [site oficial](https://www.raylib.com/) e dê uma olhada nele. Aí, vamos até o [GitHub oficial](https://github.com/raysan5/raylib/tree/master). Temos um exemplo lá, o "Olá, Mundo!" do Raylib:

    #include "raylib.h"
    
    int main(void)
    {
        InitWindow(800, 450, "raylib [core] example - basic window");
    
        while (!WindowShouldClose())
        {
            BeginDrawing();
                ClearBackground(RAYWHITE);
                DrawText("Congrats! You created your first window!", 190, 200, 20, LIGHTGRAY);
            EndDrawing();
        }
    
        CloseWindow();
    
        return 0;
    }

Mas se você tentar mandar um bom e velho `gcc test-raylib.c -o test-raylib`, vamos ter problemas!

No meu caso, deu esse problema aqui:

    /tmp/babel-IeVtjF/C-src-O6D86K.c:8:10: fatal error: raylib.h: Arquivo ou diretório inexistente
        8 | #include "raylib.h"
          |          ^~~~~~~~~~
    compilation terminated.
    [ Babel evaluation exited with code 1 ]
    /usr/bin/bash: linha 1: /tmp/babel-IeVtjF/C-bin-yCico1: Permissão negada
    [ Babel evaluation exited with code 126 ]

Não se importe muito com o ruído, é um negócio do Emacs e o Babel.

O importante é o nosso compilador reclamando que ele não encontrou o nosso cabeçalho.

Resolveremos isso da forma mais simples possível: baixando ele! Lá no GitHub, temos o arquivo que precisamos [aqui nesse link](https://github.com/raysan5/raylib/blob/master/src/raylib.h).

Eu, particularmente, nem ligo de clicar no botão de baixar. Eu vou direto no . Ele vai baixar o cabeçalho para a pasta onde você executou esse comando. Então, se precisar, pode mandar alguns `ls` e `mv` para encontrar onde está ele e colocar o cabeçalho em algum lugar que faça sentido para você. Para o nosso exemplo, eu criei uma pasta chamada `include`, como é tradição, e movi o cabeçalho para lá. As operações foram um `mkdir` e um `mv`. Fica de lição de casa você fazer isso!

Agora que você conseguiu baixar e se organizar, o meu cabeçalho está aqui assim:

    tree

    .
    ├── ch4.org
    ├── include
    │   └── raylib.h
    └── test-raylib.c

Como dito, eu tenho uma pasta chamada `include` onde está o `raylib.h` e meu programa de teste está fora dela, na minha raiz, e se chama `test-raylib.c`.

Para compilarmos o nosso exemplo, vamos fazer isso aqui:

    gcc -o test-raylib test-raylib.c

    /usr/bin/ld: /tmp/cco72c3x.o: na função "main":
    test-raylib.c:(.text+0x1e): undefined reference to `InitWindow'
    /usr/bin/ld: test-raylib.c:(.text+0x25): undefined reference to `BeginDrawing'
    /usr/bin/ld: test-raylib.c:(.text+0x4c): undefined reference to `ClearBackground'
    /usr/bin/ld: test-raylib.c:(.text+0x90): undefined reference to `DrawText'
    /usr/bin/ld: test-raylib.c:(.text+0x95): undefined reference to `EndDrawing'
    /usr/bin/ld: test-raylib.c:(.text+0x9a): undefined reference to `WindowShouldClose'
    /usr/bin/ld: test-raylib.c:(.text+0xaa): undefined reference to `CloseWindow'
    collect2: error: ld returned 1 exit status
    [ Babel evaluation exited with code 1 ]

Hmmm, ainda não está legal&#x2026;

Podemos ver ali, na primeira linha, que os símbolos não foram encontrados pelo nosso *linker* (o programa chamado ali como `/usr/bin/ld`). Então, vamos fazer duas coisas ao mesmo tempo:

    gcc -I./include -lraylib -o test-raylib test-raylib.c 

E se tudo deu certo, você deve ter visto o silêncio ensurdecedor do compilador fazendo o trabalho dele corretamente!

Lembre-se da nossa parte sobre compiladores, mas que fizemos duas coisas:

-   Pedimos para o compilador incluir um cabeçalho (ou, no caso, uma pasta com cabeçalhos), com o -I<local<sub>do</sub><sub>cabeçalho</sub>>;
-   Pedimos para o *linker* ligar nosso programa contra a biblioteca raylib usando o -l<nome<sub>da</sub><sub>biblioteca</sub>>.

Para essa segunda, você precisa baixar a biblioteca de fato. Poderíamos ligar de maneira estática, mas vamos tratar daqui para frente como programas dinamicamente ligados. Então, mande um ou equivalente da sua distribuição e seguimos em frente<sup><a id="fnr.1" class="footref" href="#fn.1" role="doc-backlink">1</a></sup>. Curiosamente, o Ubuntu, Debian, Mint e semelhantes não tem um pacote próprio, aparentemente, então será necessário compilar e instalar. Não é tão ruim assim se você já fez isso na seção anterior! 

Se tudo correu bem, você pode executar o e você verá uma coisinha assim:

![img](raylib-hello.png)

Tudo dando certo, podemos explorar melhor a biblioteca!


<a id="orged83843"></a>

# Arquitetura da Raylib

Como já falamos, a biblioteca é, na verdade, implementada como um único cabeçalho. A questão é como ela é ligada.

E, para além disso, o cabeçalho é subdividido em seções:

-   Core (núcleo);
-   Shapes (formas);
-   Textures (texturas);
-   Text (texto);
-   Models (modelos);
-   Audio (bem, áudio);
-   E mais utilidades de estruturas de dados e definições de cores.

Você pode checar a documentação aqui: [Raylib Cheat Sheet](https://www.raylib.com/cheatsheet/cheatsheet.html). Tecnicamente, a documentação é o cabeçalho de fato, e por ser uma biblioteca aberta, sempre convidamos você a ver os pormenores dela! Afinal, escrever bons programas só é possível, além de praticar bastante, ao ler bons programas.


<a id="org42a3c62"></a>

## Um pouco sobre a divisão

Você verá que para nossos projetos futuros, vamos nos deter ao uso da parte *core*, de formas e de texto. Isso é por termos os utilitários de entrada de usuário (*mouse*, teclado, tela de toque e mais), tela, arquivos (que não vamos usar, mas é útil) e boa parte da lógica de jogo. Tudo isso só no *core*! As formas são primitivos para desenhar na tela, como quadrados e círculos, mais os utilitários de adicionarmos texto para nos comunicarmos melhor com nossos usuários.

Como você pode ver, descartamos mais ou menos metade da biblioteca, e tudo bem! Nós não vamos precisar de mais que isso, então não precisamos "pagar" por isso. Nosso programa fica mais leve e rápido de compilar, nos dá menos trabalho de escrever, fica menor e, por sua vez, tem menos chance de dar errado.

Nós te convidamos a explorar a biblioteca e suas capacidades aqui, com exemplos que rodam diretamente no navegador: [Raylib Classic Games](https://www.raylib.com/games.html). Gastei alguns bons minutos no Tetris deles, mesmo não tendo todas as regras implementadas!

Tendo explorado um pouco o potencial da biblioteca, vamos dissecar algumas coisas dela.


<a id="org828384a"></a>

# Conhecendo a API

Vamos passar por exemplos práticos que estão aqui no site: [Raylib Examples](https://www.raylib.com/examples.html). Só vamos mostrar também o que você vai precisar para implementar o próximo capítulo, mas não se chateie! Caso queira se aprofundar, pegue um dos exemplos mais simples e tente modificar, compilar e rodar.


<a id="org2b99714"></a>

## De volta ao primeiro exemplo

    #include "raylib.h"
    
    int main(void)
    {
        InitWindow(800, 450, "raylib [core] example - basic window");
    
        while (!WindowShouldClose())
        {
            BeginDrawing();
                ClearBackground(RAYWHITE);
                DrawText("Congrats! You created your first window!", 190, 200, 20, LIGHTGRAY);
            EndDrawing();
        }
    
        CloseWindow();
    
        return 0;
    }

Temos já bastante material para ver, mesmo sendo só um esqueleto de programas mais complicados.

O nosso exemplo está, em ordem:

-   Declarando o ponto de entrada dele;
    -   Inicializando a janela;
    -   Enquanto a janela não precisa ser fechada:
        -   Começa a desenhar a tela;
        -   Limpa o fundo dela com a cor branca;
        -   Escreve o texto ali;
        -   Termina de desenhar a tela;
    -   Se a janela é para ser fechada, fechamos ela;
-   Tudo dando certo, o programa termina com êxito.

Entre as várias perguntas que podem ter surgido, vamos passar uma a uma.


<a id="org32bfcff"></a>

### Inicialização (e finalização)

Tudo que começa, termina, para melhor ou para pior. Nosso programa inclusive!

A parte principal é que precisamos de uma janela para ele. E para isso, temos que chamar a função que faz isso.

    int main(void){
    
      InitWindow(800, 450, "raylib [core] example - basic window");
    
      //...
    
      CloseWindow();
    
      return 0;
    
    }

Dentro da nossa tão querida `main` temos as chamadas que criam a janela e a destroem. Veja que é interessante apenas a chamada de inicialização dela ter argumentos. Isso significa que o estado não precisa ser exatamente administrado por nós, assim como não precisamos cuidar da limpeza da memória no fim. Ufa!

Sugiro dar uma olhada na documentação para entender melhor os argumentos que a `InitWindow()` recebe. Dica: você pode olhar a definição na linha 986 do `raylib.h` ou, ainda, a implementação no `src/rcore.c`, linha 604 ([disponível no GitHub do projeto](https://github.com/raysan5/raylib/blob/master/src/rcore.c)).

Você pode tentar compilar o exemplo original só com essas partes (e não esqueça do `#include`!), e nada acontecerá. Na verdade, até aconteceu, só que foi muito rápido. O programa criou uma janela e a destruiu imediatamente. Isso não é legal.


<a id="orgeba1340"></a>

### Mantendo a janela aberta

Agora, vamos ter o melhor arco de redenção da sua graduação até agora! Precisamos chamar o seu inimigo de vários EPs: o *loop* infinito!

Mas ele é um vilão reformado, então temos uma coisinha diferente:

    while(!WindowShouldClose()){
    
      //...
    
     }

Viu que temos uma sinalização ali? O nosso controle não é um simples `true`, mas algo muito parecido. Essa função `WindowShouldClose()` verifica se pedimos para fechar a janela. Como isso é pedido varia de cada sistema operacional, assim como o usuário pode chamar, como o X da janela, um comando de matar o programa e mais. O principal é que, ao mandarmos ele fechar, a função `WindowShouldClose()` se torna verdade.

Mas, como pode ver, esse comportamento está ao contrário: ela é verdade quando queremos fechar e falso quando queremos manter ela aberta. Salvos pelo `!` novamente.


<a id="org5997d59"></a>

### Fazendo algo (um pouco) interessante

Vamos ver o miolo do nosso *loop*:

    BeginDrawing();
         ClearBackground(RAYWHITE);
         DrawText("Congrats! You created your first window!", 190, 200, 20, LIGHTGRAY);
    EndDrawing();

A identação é desimportante para o programa, sendo funcional mesmo se fosse tudo uma linha só. Mas para nós, é importante manter as coisas um pouco organizadas, já que é fácil se perder.

Está vendo as duas coisas interessantes ali? Te dou alguns momentos para pensar.

Bem, dali, temos:

-   O início e fim da chamada de desenho;
-   O que realmente desenhamos na tela.

Esse modelo, eu particularmente gosto de pensar, que é como se você pedisse serviço de quarto em um cruzeiro:

-   Você liga para um número e faz seu pedido do que você quer do cardápio. Como esse pedido será transmitido e executado não importa para você;
-   Você pede todos os itens que você quer no pedido, como um hambúrguer e sopa, por pior que essa combinação seja;
-   E você avisa que é só isso e vai esperar o pedido ficar pronto.

A tela precisa ser preparada para desenhar, então avisamos o programa que precisamos rapidinho da tela. Isso é feito com o `BeginDrawing()`.

Os nossos itens são:

-   Limpe a tela e pinte o fundo de branco, com `ClearBackground(RAYWHITE)`;
-   Escreva na tela um texto, com a cor pedida e nas coordenadas desejadas;

E já que terminamos o nosso pedido, avisamos que a cozinha pode preparar ele com `EndDrawing()`.

O exemplo não está tão longe da realidade, já que você, ao fazer o pedido, provavelmente cai na mão de um maître e/ou garçom, com a cozinha recebendo o pedido, os chefs interpretando ele, pegando os ingredientes, etc. E quando tudo estiver pronto, toca o sino, manda para o pessoal da hotelaria e sobe para a sua cabine.

Um paralelo pode ser traçado sobre como você pede essas coisas à biblioteca e ela chama bibliotecas de nível mais baixo, que por sua vez, coordenam com o sistema operacional, seu processador, sua GPU e seu monitor para tudo ficar bem legal.

Viu? Até um exemplo simples já dá uma trabalheira danada, menos para a gente. Então, vamos ir um pouco mais longe.


<a id="org7221621"></a>

## Mais um exemplo simples

Acredito que mais um exemplo seja de interesse para nós. Vá até o repositório do projeto e baixe [o exemplo de uso de teclado](https://github.com/raysan5/raylib/blob/master/examples/core/core_input_keys.c). Você vai ter algo assim:

    #include "raylib.h"
    
    int main(void)
    {
    
        const int screenWidth = 800;
        const int screenHeight = 450;
    
        InitWindow(screenWidth, screenHeight, "raylib [core] example - input keys");
    
        Vector2 ballPosition = { (float)screenWidth/2, (float)screenHeight/2 };
    
        SetTargetFPS(60);               
    
        while (!WindowShouldClose())   
        {
            if (IsKeyDown(KEY_RIGHT)) ballPosition.x += 2.0f;
            if (IsKeyDown(KEY_LEFT)) ballPosition.x -= 2.0f;
            if (IsKeyDown(KEY_UP)) ballPosition.y -= 2.0f;
            if (IsKeyDown(KEY_DOWN)) ballPosition.y += 2.0f;
    
            BeginDrawing();
    
                ClearBackground(RAYWHITE);
    
                DrawText("move the ball with arrow keys", 10, 10, 20, DARKGRAY);
    
                DrawCircleV(ballPosition, 50, MAROON);
    
            EndDrawing();
    
        }
    
        CloseWindow();        
    
        return 0;
    }

Esta é a forma mais simples dele. Saiba que os direitos de reprodução estão sob a licença libpng/zlib, e é de autoria do  Ramon Santamaria (@raysan5), Copyright (c) 2014-2025. A modificação foi feita apenas para facilitar a visualização.

Também, vamos tratar apenas das partes que você não deve ter visto, para não nos repetirmos em relação à parte anterior.


<a id="org951e839"></a>

### `SetTargetFPS()`

Para esse exemplo, nada muito complicado será feito com essa função. Entretanto, ela é importante se você está fazendo um jogo que depende de física.

Isso é, em partes, por motivos históricos, e outra parte por motivos de praticidade. Há muito tempo, programas tinham sua velocidade ligada ao *clock* da CPU. Isso não é exatamente um problema a primeiro momento.

Um programa de planilhas como o Lotus 1-2-3, o avô do Microsoft Excel, é meio indiferente se o processador é lento ou rápido. Porém, programas que dependem de tempo são muito mais sensíveis. Pense em um jogo onde você tem que apertar um botão que abre uma porta, que se fecha lentamente, e você tem que correr para atravessar ela e sair da sala. Se você está em um i386, o avô de todos os Intels, a 16MHz, tudo bem. Contra um AMD Ryzen qualquer coisa que chega até 5GHz, pouco mais de 300 vezes mais rápido, esse desafio fica complicado se a porta se fechar com essa diferença de velocidade. 

Então, é ideal que separemos a velocidade do nosso *hardware* do nosso programa. Até mesmo porque não conseguimos prever que tipo de máquino nosso usuário estará usando.

Para manter essa experiência consistente, o `SetTargetFPS()` é essencial. Ele nos garante que não ultrapassaremos essa velocidade limite. Para o exemplo, ela é 60 FPS (ou Hz).

Se estivéssemos vendo um exemplo com física, como os outros [na página de exemplo da Raylib](https://www.raylib.com/examples.html), precisaríamos da irmã dessa função, que nos diz quanto tempo passou entre quadros desenhados. O exemplo **delta time** nos mostra isso. Se quiser quebrar um pouco a cabeça e brincar com ele, é importante. Eu não acho a matemática intuitiva até o momento de rolar a roda do *mouse*. Aí você entende a importância desse trabalho todo.

O excerto abaixo nos dá uma ideia melhor do que queremos dizer. Ele é de um outro exemplo solto, então não se desespere:

    deltaCircle.x += GetFrameTime()*6.0f*speed;
    // This circle can move faster or slower visually depending on the FPS
    frameCircle.x += 0.1f*speed;

Ele tem que funcionar junto com o `SetTargetFPS()`. O `GetFrameTime()` nos dá, em segundos, o tempo decorrido entre cada quadro. Então, se queremos ter 60 quadros por segundo, algo trivial para o nosso exemplo, teremos 16,6&#x2026;ms entre cada um, ou 0.016s. Já a outra função é mais rápida por ficar na base da sorte o *framerate*. Ou seja, depende exclusivamente da velocidade da máquina e de objetos na tela. Então, temos que usar esse valor entre quadros para tornar consistente a simulação.

Bem, chega de falar de matemática com tempo. Ela fica bem confusa bem rápido! Então, entenda apenas que é uma péssima ideia você (querendo ou sem querer) associar a lógica da física diretamente com a velocidade de renderização. As coisas ficam inconsistentes rápido. Prefira fazer contas com a variação de tempo e você terá melhores garantias.

E não esquente, esse excerto não é do exemplo que estávamos vendo antes, mas sim está aqui para ilustrar a necessidade de um `SetTargetFPS()`.


<a id="orge491d1d"></a>

### Desenhando e movendo a bola

Bem, queremos que a bola faça duas coisas:

-   Apareça em algum lugar da tela;
-   Mova-se pela tela segundo o que pressionarmos das setas.

1.  Apresentando a bola

    Como estamos em C, precisamos definir a variável que guardará o centro da bola:
    
        Vector2 ballPosition = { (float)screenWidth/2, (float)screenHeight/2 };
    
    Não estranhe que ela é um `Vector2`, mesmo sendo um ponto. Para um computador, um ponto de duas coordenadas e um vetor são a mesma coisa. A Raylib facilita para a gente ter só `Vector2`, mas se usarmos o tipo para representar pontos, como é o caso, precisamos tomar cuidado para não fazer besteira com contas com vetores de fato.
    
    Também note que precisamos fazer um *cast* de `int` para `float`. Nesse caso, os valores são bem definidos, então não é perigoso/indefinido.
    
    Agora, queremos desenhar ela:
    
        DrawCircleV(ballPosition, 50, MAROON);
    
    Vá até a documentação e entenda os argumentos. Eu espero.
    
    No nosso caso, ela é do tipo<sup><a id="fnr.2" class="footref" href="#fn.2" role="doc-backlink">2</a></sup> `V` ali, então ela vai receber o nosso vetor de centro da bola. Note também que ela mora dentro do *loop* principal, entre o início e fim do desenho, já que queremos que ela apareça na tela toda vez que a tela for redesenhada. Se quiser, mexa na posição dessa função e veja o que acontece! Aqui, até te dou uma ajuda:
    
        printf("Posição da bola:\tX:%f\tY:%f\r", ballPosition.x, ballPosition.y);
    
    Ela vai te dar a posição da bola no console, mesmo se você não conseguir ver ela se mexendo de fato. Não esqueça de dar um `#include <stdio.h>`!

2.  Movendo a bola

    Bem, queremos movimentar a bola, se não a graça foi perdida:
    
        if (IsKeyDown(KEY_RIGHT)) ballPosition.x += 2.0f;
        if (IsKeyDown(KEY_LEFT)) ballPosition.x -= 2.0f;
        if (IsKeyDown(KEY_UP)) ballPosition.y -= 2.0f;
        if (IsKeyDown(KEY_DOWN)) ballPosition.y += 2.0f;
    
    Três coisinhas são legais aqui:
    
    -   O uso de `if` ao invés de uma escada ou de `switch / case`. Por quê? (Dica: e se eu apertar para cima e para baixo ao mesmo tempo?)
    -   Os macros para reconhecermos os botões são bem intuitivos, e isso é feito para não termos que quebrar a cabeça e descobrir todas as possibilidades de onde essas teclas podem estar no teclado;
    -   Elas ficam dentro do *loop* para conseguir responder de maneira dinâmica às mudanças de estado de jogo.


<a id="org4c4f6e5"></a>

## Finalizando a seção

Você entendeu melhor um pouco como um jogo responde às entradas de um usuário, na perspectiva de quem programa. Então, vamos deixar a bola (entendeu? O exemplo é sobre uma bola) contigo: mexa um pouco no exemplo, troque a cor, desenhe outro tipo de forma, mude os tipos de botões, altere a velocidade, etc.

Não vamos te impedir de seguir para o próximo capítulo se você não fizer isso, mas recomendamos muito que você mexa nesse singelo exemplo. Ele é muito didático para você sentir o ritmo da biblioteca. Acostume-se, que o próximo capítulo, vamos fazer *vida*!

Boa sorte!


# Footnotes

<sup><a id="fn.1" href="#fnr.1">1</a></sup> Pode ser meio irritante e confuso de primeira, mas já que C é uma língua simples, seus compiladores tendem a oferecer, em primeiro momento, comportamentos bem simples. Você pode complicar o quanto você quiser no futuro, mas isso não é um curso de `make`, `cmake`, análise estática, `clang-tidy` ou CI (veja nossa trilha de Git!).

<sup><a id="fn.2" href="#fnr.2">2</a></sup> Chamar ela de "tipo" pode te induzir ao erro. Talvez o mais correto seja "família", já que tem a ver com funções que usam vetores para fazer isso. Peço desculpas aqui se alguém pensou que isso pode significar Notação Húngara para nomes de funções. Isso é coisa da Microsoft e certos tipos de repositórios. Esse não é o caso.
