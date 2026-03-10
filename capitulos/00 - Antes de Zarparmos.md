<tt>
	     ..
	  .--%%%-xm
	%%#m.x*x%x%m.
	x%..x	. ..
    #. .
    %#x .
    -m%#-x		      .x. x.--	-	   ...x.. ..
	  x%#%.x.	   x..*#x#xx#x#%x-	  .#.x-mm--
	   -x-#-%.	   -x-m...x  .-x#	  -m-x-.%m## .
	     ...m%%*	  .# .	.*.-.-x#*	  ..   .m*%#x
  .*%.		.xmmxm	  .*	 m--x-*#-     .. x - x- mmm%-
  -#.  .	   *-m.	  .#-.	 . -.--.     -mx#*m*%#m-#x   .
  .mxmm-  -..---- *%-%%	  .x#..		     ##*.xm--*m##.-                                x#m--m*xm%-
    xm#%**#*m#m###mxm--	   x**%x% - . .	   .x*..x.   .xx.m. .... .    		     x###############mm-.%.
    . .m-.   ..	 xm*-	     .m#-*%%*%m.   .-##.-..-..%.#mxx.mxmm%%		    ##*####*################*#-x
		 ..	      -..x..m ..    %x#%###%**mm.-mm%*x-mm.		   #######*################*####*..
					      .-  m-  .. --.  . .		-############m-##%x%.#%#.##########%m
									      xm#########*#%*	       -xx#x########m
									     m#######%%%*x		    .m-#####%
									     ########%*x		      mx-xxm
			      .mxm-x-...-				   x%#######--
			     %.#**xx%#-%--				   x%#######
			    .-x####m*##%x				  ..######%-.
			     .##%-.- .	-				  .x#####%#-.
			     .#*%					   *#######x.
	 -  .-	-.	     .%##x.					   xm####*#.m.
      .	x#x##%#%-- .	       *x#*+.         				  . %#####%m-.
    -.x#%##xx#-%*%#-.	     .+++-##*#**%%m%*%	              		   --######*#*.-
    .m##-- ... .xx%m	 . %%#+##########mm.--.	    x-x           	    -m######*x-%.		  #x%x.--
   ..%%x	  %-.	  +.#m#-#%##-.        	    | |            	     m.#######***xx%-- -.x.--xxx#m-%#*.#*
   m.x.-.      - m#m	        .-*#.-.   	  x-----------x    	      m*-##########%* #m%..%%.**###*m###*m
   .-#m.%* .  .---x	     	.-xx-     	  | o  o  o  o|      	       .%xx#########################-##%m-
     x.*m-%mxx**mm-	      	- *%%..    	\-+-\ 	    /------- 		  ..-*%**########*###%########%x
      .. .-*xx---	        +m*+%-        -. \   -------    / 		     -xm.--*%#xxx%#%###*#-xx*
             ..-	      - ###%--      - ...-\. . . .-   -/  . -- .  .	         xm      --x m..
			      m####m.	   .-  .-.-.-m++m--.--.	....++.--
			      -#%%%-.	    -  .-..


	
</tt>

# Índice

1.  [Capítulo 0](#org77fa941)
    1.  [Comandos Básicos do Linux](#org34a13c4)
        1.  [Terminais](#org6d07fb3)
        2.  [Instalando um compilador](#orgc58d3cb)
        3.  [Usando o Terminal e Rodando Comandos](#orgb89f60c)
    2.  [Álgebra Booleana Básica](#org3c38bb5)
        1.  [Valores Possíveis](#org5598e57)
        2.  [Operações Possíveis](#org94689e3)
    3.  [O Computador de Von Neumann](#org33f335a)

<a id="org77fa941"></a>

# Capítulo 0

Olá, *gamer*!

Seja bem vinde ao curso introdutório de C da Conway!

Acreditamos que esse seja o seu primeiro contato formal com a linguagem C. Caso não seja, esperamos que seja um momento exploratório e de revisão da linguagem.
Caso o conteúdo seja básico demais, sugerimos duas coisas: leia rapidamente a parte de C do curso e pule direto para a parte de Raylib; e caso queira se aprofundar na linguagem, temos dois livros de recomendação, em nível de profundidade crescente: Effective C, 2ª Ed., por Robert Seacord (inspiração do nome!) e Modern C, por Jens Gusted ([disponível aqui](https://inria.hal.science/hal-02383654v2/file/modernC.pdf)). Ambos trabalham no comitê do padrão da linguagem, então consideramos muito a palavra deles.

Caso você nunca tenha nem mesmo mexido em um computador que não um celular ou tablet, não se desespere! Vamos te guiar pelo Bêabá que você precisa seguir para conseguir escrever, compilar e rodar programas em C com confiança!

Espero que você se divirta!

---

<a id="org34a13c4"></a>

## Comandos Básicos do Linux

No próximo capítulo, vamos falar um pouco mais da história da linguagem e o porquê de preferirmos Linux para esse caso. Entretanto, temos que conferir algumas coisas antes de zarparmos na nossa viagem, de acordo com a sua máquina.

Todas as plataformas modernas tem alguma forma de produzir e rodar os programas que vamos fazer. Pelo menos, nessa primeira parte.

Escolha, primeiro, um editor de texto. Podem usar os que já estão incluídos no seu sistema operacional, já que eles são de pouca importância para esse curso.

O Visual Studio Code é bem popular. Particularmente, eu (Thiago) gosto de usar GNU Emacs. Temos colegas que usam VIM, Neovim e variantes.
O importante é que ele não seja um *processador* de texto, como o Microsoft Word, LibreOffice Writer ou Google Docs. Eles são uma péssima ideia para produzir código. Pense que, superficialmente, eles podem ser parecidos, mas são tão semelhantes quanto um ventilador e um liquidificador.

Só precisamos garantir aqui uma certa homogeneidade com os ambientes de interface de texto, conhecidos como terminais ou consoles.



<a id="org6d07fb3"></a>

### Terminais

Por mais que seja possível usarmos ambientes gráficos, a experiência ainda é aquém daquela que o terminal nos permite. E mesmo se formos usar um GUI (Graphical User Interface, ou Interface de Usuário Gráfica), no fundo, ela está passando comandos de texto para nossos compiladores.

Queremos que você conheça a forma mais simples de fazer tudo funcionar, então vamos nos manter a isso.

Caso você não tenha acesso a um computador capaz de rodar Linux (ou não queira, entendemos também), vá até as salas da pró-aluno, no primeiro andar (não no térreo) do Ciclo Básico. Lá, temos computadores de uso exclusivo para nós de SI, com isso tudo já instalado nas partições de Linux. Essa é a forma mais fácil, mesmo que fisicamente distante, de fazer esse curso. Acreditamos também que ela pode ser a sua última opção, se qualquer uma dessas opções a seguir não te ajudar.

Mas, lembre-se: pedimos encarecidamente que você faça esse curso em Linux (ou UNIX-like), ficando evidente ao longo da trilha.

**Temos aqui um pequeno curso de linha de comando no Linux: [Linux Journey - Command Line](https://labex.io/lesson/the-shell). Faça ele depois de instalar da forma que explicamos aqui embaixo.**

- Android

    Sim, é possível compilar e rodar nossos programas em plataformas Android.
    
    Baixe o [Termux](https://termux.dev/en/), disponível na [Play Store](https://play.google.com/store/apps/details?id=com.termux&hl=pt_BR) e na [F-Droid](https://f-droid.org/pt_BR/packages/com.termux/), um editor de texto de código já deve estar instalado, como o VI. Sugerimos que você busque usar outro, mais completo um pouco, como o VIM, Neovim ou Emacs.
    
    Acostume-se a baixar pacotes com ele e aí podemos seguir.

-  Linux

    Parabéns, nada precisa ser feito! Pelo menos, para instalação.
    
    Pedimos que você se acostume com um terminal (é só procurar por "terminal" no seu lançador de programas) e tenha seu editor de texto de preferência a mãos.

-  Mac

    Parabéns também! Nada há de ser feito. Isso é porque o Mac e o Linux tem um ancestral comum: o UNIX.
    
    Você também não precisa fazer mais nada, além de se acostumar com o terminal e escolher um editor de texto.

-  Windows

    Temos duas formas de fazer isso funcionar:
    
-  WSL2
    
    Em versões mais modernas de Windows, em computadores fabricados depois de 2010, é possível utilizar uma máquina virtual minúscula desenvolvida pela própria Microsoft.
        
    Essa é a nossa forma predileta de rodar os programas do curso no Windows 10 e Windows 11.
        
    Siga o tutorial oficial e escolha, se possível, uma máquina Ubuntu. Elas são as mais fáceis de utilizar.
        
    O tutorial oficial está aqui: [Como instalar o Linux no Windows com o WSL](https://learn.microsoft.com/pt-br/windows/wsl/install).
        
    Caso esteja usando o VS Code, há uma integração legal com o editor, que será reconhecida automaticamente.
    
-  MSYS2
    
    Caso você não consiga instalar o WSL2, seja por falta de virtualização ou versão do Windows, vamos ter que instalar esse cara aqui: [MSYS2](https://www.msys2.org/).
       
    No caso, execute até o fim as instruções de instalação e isso, além de te dizer que está tudo certo, já vai te dar o GCC.

---

<a id="orgc58d3cb"></a>

### Instalando um compilador

Independente da plataforma, precisaremos de um compilador de C. Eles são abundantes, mas vamos nos concentrar em um: GCC, originalmente GNU C Compiler, mas agora GNU Compiler Collection.

Só o pessoal do Android que vai ter que usar o CLang. Ele não é pior nem melhor que o GCC, mas diferente. Eles, para nossos exemplos, são bem intercambiáveis, bastando trocar o `gcc` por `clang` nos comandos.

-  Linux

    Parabéns, você não precisa fazer nada! Ou, na verdade, quase nada.
    
    O seu sistema operacional é C, puro e simples.<sup><a id="fnr.1" class="footref" href="#fn.1" role="doc-backlink">1</a></sup>
    
    Cada distribuição tem seu próprio gerenciador de pacotes. Acostume-se com ele, podendo ser, em geral, `apt` (para Debian, Ubuntu, Mint e amigos), `dnf` (Fedora e OpenSUSE) ou `pacman` (Arch).

-  Android

    É semelhante ao Linux, então veja lá. Só no caso do Termux, você vai ter que usar o `clang` como compilador e o `pkg` como gerenciador de pacotes.

-  Mac

    Não tenho muita propriedade de causa, mas você vai ter que instalar o Brew antes. [Instale ele aqui](https://brew.sh/).
    
    Aí, siga aqui o [tutorial no Code Forces aqui](https://codeforces.com/blog/entry/101012).

-  Windows

    - WSL2
    
        Use a instrução da parte de Linux, de acordo com a sua distribuição escolhida.
    
    - MSYS2
    
        Se você já fez a instalação completa, você já baixou o GCC, então está tudo em ordem.

---

<a id="orgb89f60c"></a>

### Usando o Terminal e Rodando Comandos

Caso não tenha visto, siga o tutorial aqui: [Linux Journey - Command Line](https://labex.io/lesson/the-shell). Depois de fazer, olhe rapidamente aqui embaixo, que temos um pouco de história e alguns conceitos importantes.

Independentemente da plataforma, todos os terminais tem a mesma ideia: o sistema operacional oferece programas (chamados de "comandos" também), dos quais você digita o nome e opções, com o computador os executando e te devolvendo o resultado logo na(s) linha(s) seguinte(s).

Um pequeno exemplo de usar o comando que me diz meu nome de usuário:
```bash
    [coscal@mothership ~]$ whoami
    coscal
    [coscal@mothership ~]$ 
```
Meu usuário e mais alguns dados estão entre `[]`. Especificamente, `[usuário@nome_da_minha_máquina diretório_em_que_estou]privilégio_do_usuário`. O `$` indica que não estou como um super usuário (ou administrador), mas sim um usuário regular.
Ao fim da linha, `whoami` é o programa que me devolve meu nome de usuário. Meu usuário está logo na linha seguinte, já que é o resultado do programa. Por fim, o terminal me devolve uma linha limpa, para poder pedir mais comandos.

Essa é a forma original de interação com o computador por causa de terminais de teletipo, uma máquina que transmitia texto por linhas telefônicas e de código Morse. O nome "terminal" surge da ideia de que cada ponta (ou, cada "término") do fio telefônico tinha uma máquina de teletipo (o "terminal").

Já que esse equipamento já existia, decidiram conectar no computador. Isso era milhares de vezes mais agradável que ter que virar as chaves individualmente ou perfurar baralhos imensos de cartões Hollerit para transmitir um programa ao computador.

Não só isso, era possível, especialmente em universidades e empresas, distribuir esses terminais de teletipo (se eles já não estivessem espalhados por causa do seu propósito original) e conectá-los ao prédio da computação e permitir seus usuários transmitirem comandos sem terem que andar centenas de metros. Conecte em uma linha telefônica e você pode atravessar continentes para mandar seus comandos. Mas a história da Internet fica para outro dia.

Essa infraestrutura de comandos de texto ainda é utilíssima, tendo seu devido local. Arquivos de configuração automática, *datacenters*, acesso remoto e muito mais ainda são usos comuns de terminais.

Seu sistema operacional já vem com vários comandos/programas. É comum você poder apertar TAB múltiplas vezes e receber uma lista de comandos disponíveis.

Caso não tenha, vamos mostrar alguns comandos simples para mostrar suas pastas (chamados de diretórios) e a hierarquia de arquivos.
```bash
    ls ; # LiSt, lista os arquivos e diretórios no diretório atual
    pwd; # Print Working Directory, imprime o caminho completo do diretório atual
    cd <diretório>; # Change Directory, muda para o diretório
    whoami; # Who Am I, imprime seu nome de usuário na tela
```
Duas coisas importantes do exemplo:

-   Quando o computador nos devolve o resultado do programa em forma de texto, dizemos que ele "imprimiu na tela". Lembre das máquinas de teletipo e como elas eram impressoras com telefones;
-   Os programas tendem a ser palavras, pequenas frases, siglas ou mnemônicos em inglês, para facilitar você se lembrar.

Sabendo um pouco desses comandos, vamos passar aqui um exemplo interessante:
```bash
    ls;
    ls -l;
    ls -la;
    ls -la --human-readable;
```
O resultado:
```bash

# ls
#ch0.org#

# ls -l
total 12
-rw-r--r-- 1 coscal coscal 9851 mar  5 18:33 #ch0.org#

# ls -la
total 16
drwxr-xr-x 1 coscal coscal   36 mar  5 15:53 .
drwx------ 1 coscal coscal  652 mar  5 17:42 ..
-rw-r--r-- 1 coscal coscal 9851 mar  5 18:33 #ch0.org#
lrwxrwxrwx 1 coscal coscal   34 mar  5 15:52 .#ch0.org -> coscal@mothership.16277:1772724224

# ls -la --human-readable
total 16K
drwxr-xr-x 1 coscal coscal   36 mar  5 15:53 .
drwx------ 1 coscal coscal  652 mar  5 17:42 ..
-rw-r--r-- 1 coscal coscal 9,7K mar  5 18:33 #ch0.org#
lrwxrwxrwx 1 coscal coscal   34 mar  5 15:52 .#ch0.org -> coscal@mothership.16277:1772724224
```

O primeiro resultado é o mais simples, que nos dá o resultado do comando `ls`, executado na pasta onde estou escrevendo esse capítulo.

O segundo, é resultado do comando `ls -l`. O `-l` é o que chamamos de "argumento". Se `ls` é uma função do tipo f(x), o `-l` é esse x. Para esse comando, podemos passar mais de um argumento, então pense em f(x, y, z, &#x2026;).

Quatro coisas devem ser ditas sobre esses argumentos:

-   Geralmente, passamos eles com um hífen. Também é possível, para alguns comandos, fazermos isso sem esse traço, como o `tar`, que historicamente recebe um emaranhado de letras, ou o `systemd`, que recebe palavras inteiras;
-   A ordem não importa. `-la` e `-al` são equivalentes para `ls`. Isso é algo comum (mas não garantido) à maioria dos programas de terminal;
-   Essas letras podem ser confusas agora, mas são mnêmonicas: `l` significa `list` (formatar em lista) e `a` significa `all` (tudo que há na pasta);
-   Muitos argumentos têm também a versão por extenso. Por exemplo, `--human-readable` (legível por gente) tem o mnemônico `h`.

Também é comum termos um comportamento padrão para os programas. Por exemplo, há um sistema bem complexo de dar diretórios aos programas, comuns ao terminal. Tente executar `ls .` e você verá que o resultado é igual. Isso é por que o `ls` tem como padrão o diretório atual. Você ainda pode copiar o resultado do `pwd` como argumento para o `ls` e o resultado será o mesmo. O terminal é uma interface completa de programação de respeito, então você pode até mesmo fazer `ls $(pwd)`, ao invés de colar o resultado. Programação `bash` também foge desse tutorial.

Explore um pouco os comandos! O terminal tende a te avisar se você está fazendo algo errado.

E caso queira conhecer um pouco mais argumentos, opções, funcionalidades e mais dos programas de terminal, muitos tem manuais.
```bash
    man <programa>; # MANual, vamos usar bastante ele para algumas funções de C também
    info <programa>; # INFOrmation, informações sobre um programa
    
    [programa] --help; # Ajuda de um programa, argumento bem comum para eles
```
Experimente um pouco esses comandos de ajuda. Eles são muito úteis.

Um exercício legal é você mandar um `man man` ou `info info` e ver o que eles explicam sobre eles mesmos!


<a id="org3c38bb5"></a>

## Álgebra Booleana Básica

O sistema binário não é uma escolha feita ao acaso para representar informação em um computador. Você terá a graduação inteira para descobrir os milhares de motivos.

O que nos importa agora é como ela opera na sua forma mais simples.


<a id="org5598e57"></a>

### Valores Possíveis

Toda a álgebra Booleana possui apenas dois valores possíveis, opostos, chamados de valores-verdade: FALSO (0) e VERDADEIRO (1). Você pode ver que cada um tem um valor numérico designado.

Variáveis podem ter valores fixos ou expressões. Vamos escrever variáveis como X, Y e mais para representar valores em funções e operações.


<a id="org94689e3"></a>

### Operações Possíveis

Muitas das operações são equivalentes entre si de uma forma ou outra, através de composição. As mais simples, temos três, representadas em tabelas:

-   NOT (NÃO / NEGAÇÃO)

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">X</th>
<th scope="col" class="org-right">NOT(X)</th>
</tr>
</thead>
<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>
</tbody>
<tbody>
<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>
</tbody>
</table>

-   AND (E)

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">X</th>
<th scope="col" class="org-right">Y</th>
<th scope="col" class="org-right">AND (X, Y)</th>
</tr>
</thead>
<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>
</tbody>
<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>
</tbody>
<tbody>
<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>
</tbody>
<tbody>
<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

-   OR (OU)

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">X</th>
<th scope="col" class="org-right">Y</th>
<th scope="col" class="org-right">OR (X, Y)</th>
</tr>
</thead>
<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>
</tbody>
<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>
</tbody>
<tbody>
<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>
</tbody>
<tbody>
<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

Essas expressões tem X e Y comutativos (não importa a ordem).

Essas funções podem ser compostas para resultados mais complicados: NOT(AND(1,1)) = 0.

Também podemos escrever elas rapidamente de forma algébrica. A expressão acima: (1 \* 1)' = 0. Note que as aspas singulares (ou apóstrofo, tanto faz) representam a inversão da expressão dentro do parênteses. É como adicionar o "-" na álgebra normal a um número, como -(1) = -1. Ela fica escrita como 0' = 1 e 1' = 0. Para facilitar a visualização, usamos parênteses como (1)' = 0 e (0)' = 1.

O OR é equivalente à soma: (0 + 1) = 1, e o AND à multiplicação: (0 \* 1) = 0. A beleza dessa representação é que ela é bem fácil de ver, por conhecermos algebra regular. Por exemplo, me diga o resultado de (1 + 0 + &#x2026; + 0) e (0 \* 1 \* &#x2026; \* 1). Um e zero, respectivamente.

Com isso, você pode construir toda a computação digital que já exisitiu e vai existir.

Vamos usar esse conhecimento para dar poder de escolha para nossos programas, realizando algo de acordo com o valor-verdade de uma expressão ou outra coisa se for o valor oposto.


<a id="org33f335a"></a>

## O Computador de Von Neumann

Nome do matemático e físico húngaro John von Neumann (pronunciado "Nóimãn", e não "Núumãn"), ele concebeu um computador bem simples e que é uma forma abstrata da maioria das máquinas computacionais modernas.

Elas tem memória e processamento. Essa memória guarda informação, como dados e programas, e o processador, conectado à memória, pega conjuntos de instruções (os programas) e executa o que eles pedem. Muitas vezes, eles pedem para alterar os dados na memória.

A nossa memória é como uma estante, onde cada prateleira cabe um número bem limitado de livros<sup><a id="fnr.2" class="footref" href="#fn.2" role="doc-backlink">2</a></sup>. Para que o nosso bibliotecário encontre as informações importantes nessa imensa biblioteca que é a memória, é necessário termos endereços para comunicar a localização das coisas.

```
 |----------+------------|
 | Endereço | Informação |          +----------------+
 |----------+------------|     	    |                |
 | 0        | X          | <--------+  	     +-------+-----+
 |----------+------------|                   |             |
 | 1        | Y          |                   |             |
 |----------+------------|                   |     CPU     |
 | ...      | ...        |                   |             |
 |----------+------------|                   |             |
 | n        | Z          |----------+        +-------+-----+
 |----------+------------|          |               /|\
                                    +----------------+
```

A CPU (*Central Processing Unit*, o seu processador) pede informação guardada na memória para o controlador que mora na memória. As informações podem ser instruções ou dados. Se for uma instrução, o processador precisa também pedir os dados complementares à memória. Ao ter tudo em mãos, ele processa os dados segundo a instrução e devolve o resultado para a memória. Pense em você fazendo contas manualmente, como uma soma de números grandes em uma prova. Você pega os dados no enunciado, arma a conta, processa os números e escreve o resultado no campo de resposta.

A forma exata como que a CPU pega a próxima instrução do seu programa é de pouca importância para nós, assim como os pormenores de acesso à memória. O que importa é que cada lugar para guardar informação na memória tem um endereço, variando de 0 a N, e na prateleira do endereço temos informação.

Um dos problemas graves de uma forma de implementar a arquitetura de von Neumann é que dados e instruções ficam misturados. Esse design é fácil de implementar por não termos essa distinção, mas coisas estranhas podem acontecer. Por exemplo, o que significa (<del>) + (</del>)? Uma soma de sinais de soma não faz sentido.

E a CPU é simples demais para saber a diferença de dados e instruções, já que a arquitetura não exatamente diferencia elas.<sup><a id="fnr.3" class="footref" href="#fn.3" role="doc-backlink">3</a></sup>

Entretanto, há uma convenção simples de como organizamos seções dos programas na memória, que chamados de segmentos:

```

 Endereço
            |------------|
 Perto de 0 | Metdados   | <-- Ajuda o sistema operacional a colocar o programa na memória, falando o fomato dele, onde ficam certas informações dentro dele e mais.
            |------------|
            | Instruções | <-- O programa de fato, com as operações, funções e mais.
            |------------|
            | /Heap/     | <-- Parte dinâmicamente alocada. Se o programa precisar de mais memória, ele usa daqui
            |------------|
            |    ...     | <- Espaço entre o /stack/ e o /heap/. Isso premite o /stack/ ou o /heap/ crescer, até chegar perto um do outro
            |------------|
            | /Stack/    | <-- A pilha, onde vão ficando as chamadas de funções e seus argumentos
            |------------|
 Perto de N | Dados      | <-- Dados constantes que você usa no seu programa, como números escritos direto nele
            |------------|
```

Pense que os metadados ficam mais próximos do 0 e os dados constantes ficam mais perto de N. O *heap* é aumentado na direção dos endereços mais pertos de N, e a pilha cresce para endereços mais perto de 0. Por isso que dizemos que "a pilha cresce para baixo".

Com essa convenção, temos uma separação do que são instruções e dados, resolvendo o principal problema da nossa arquitetura.

Mas ainda temos um problema grave: queremos que nossos programas sejam bons a ponto de aceitar vários tipos de entrada. Por exemplo, vamos dizer que você tem um programa que o usuário usa para contar a quantidade de palavras de um texto de tamanho qualquer. Queremos que ele funcione não só para *tweets* individuais, mas também para todos os trabalhos do Machado de Assis e textos maiores.

Quando o programa encara esse problema de um texto imenso, a lógica é a mesma do pequeno, mas ele precisa guardar na memória todo Machado de Assis. Para isso, medimos o tamanho dos arquivos, que é fácil (podemos pedir para o sistema operacional), e com essa informação, pedir para o sistema operacional nos dar um espaço no *heap* (nome para monte, amontoado) do tamanho dos textos e, depois que ele aumentar o tamanho do *heap*, jogamos eles ali dentro e começamos a processar.

Há um problema, no caso, se decidirmos só chamar uma função (isso ficará claro depois o que significa), cujo um dos argumentos são todos os textos de Machado de Assis. Já que todos os argumentos de funções são colocados na pilha (ou *stack*), pode ser grande demais e bater com o *heap*, ou pior, direto nas instruções. Se alguma dessas coisas acontecer, o sistema operacional mata o seu programa, gerando um de dois erros:

-   Se a pilha cresceu demais e atingiu os outros segmentos, temos um *stack overflow*;
-   Se o programa faz uma operação ilegal, como tentar acessar memória inválida (e vamos falar o que isso significa depois), temos uma falha de segmentação, ou *segmentation fault* (ou só *segfault*);

Nós temos essa diferença porque os mecanismos de acesso à essas memórias é diferente. A pilha é facilmente acessível ao programa, podendo colocar ou tirar dados dali livremente. Mas o *heap*, ao mesmo tempo que ele é imensamente grande, se não for grande o suficiente para o que precisamos, o sistema operacional pode ter que realocar o programa para um lugar que cabe, ou, pelo menos, dizer outro lugar que o seu programa pode usar e que cabem os dados.

Pense em um quarto de hotel. Se é para uma pessoa apenas, provavelmente um quarto com duas camas e um banheiro é mais do que o suficiente. Entretanto, se essa pessoa for apenas um agente (um tanto quanto incompetente e esquecido) de uma banda famosa que vai chegar, vai precisar de mais quartos pouco antes de seus artistas chegarem. Ainda pior, esse agente vai precisar pedir para o hotel mais quartos para os funcionários e um armazém para os instrumentos e equipamentos. Mas, enquanto não há a necessidade, ele não precisa pedir nada para a equipe do hotel.

Já que essa é realmente uma parte chata da programação, muitas linguagens mais modernas automatizam esse processo para a gente. Ainda mais quando temos a chance de esquecer de pedir mais memória ou avisar o sistema operacional que terminamos de usá-la.

O C nunca foi e nunca será uma delas. Mas não tema, isso tem suas vantagens: se você tem controle da memória, você pode otimizar o seu programa de uma maneira impossível em qualquer outra linguagem. Não só isso, mas também é possível programas muito pequenos, importante para sistemas embarcados e sistemas operacionais.

Se você não entendeu o papel da pilha e do *heap* ainda, tudo bem. É abstrato mesmo. Siga com a trilha e, inevitavelmente, *stack overflows* e *segfaults* acontecerão. Não se assuste! Só a prática vai te ajudar a realmente entender melhor os mecanismos da memória do computador.

Nos próximos capítulos, vamos tratar de como a linguagem C permite falarmos com o processador e pegar a memória que precisamos, de maneira bem fácil. Acredite, mesmo que você não queira seguir com isso para o resto da sua carreira, aprenda mesmo que seja só para tirar uma boa nota nas disciplinas de IP e AEDI e AEDII, assim como OACI e OACII.


# Notas de Rodapé

<sup><a id="fn.1" href="#fnr.1">1</a></sup> Tecnicamente, agora temos Rust no kernel também, já há alguns anos. Acreditamos que é uma mudança positiva, mas para fins práticos, o kernel é primariamente em C. Novamente, questões históricas e o motivo disso serão explicados no próximo capítulo.

<sup><a id="fn.2" href="#fnr.2">2</a></sup> Não importa muito quanto, mas tende a ser um múltiplo do que chamamos de "tamanho natural" do processador, como 32-bit ou 64-bit. A analogia começa a quebrar muito rápido se você ficar pensando demais na equivalência "bytes, bits, inteiros, floats e tamanho natural" com "livros". O importante é que as nem as prateleiras e nem as estantes são infinitamente grandes, por mais que o Google Chrome ache que são.

<sup><a id="fn.3" href="#fnr.3">3</a></sup> Há um debate sobre as arquiteturas de Harvard, um modelo também abstrato de computação que separa explicitamente nossos programas em memória de dados e de instruções. No nosso caso, ela não é super relevante, a menos que você esteja usando um microcontrolador ou um processador MIPS.
