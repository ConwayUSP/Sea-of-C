# Conhecendo o Terreno

Agora que sua mochila já está pronta e o mar está a sua frente, **chegou a hora de navegar!!!** _Só que não..._, antes de colocarmos a mão na massa com o C, vamos antes sentar na sala do capitão e dar uma olhada no mapa irado e estranhamente velho do terreno e das correntes marítimas adiante. O que estou querendo dizer é: vamos entender um pouco do que É a linguagem C, e porque ela é importante.

Neste breve capítulo, iremos abordar:

- Uma breve história da linguagem
- Características importantes do C

## Uma breve história da linguagem

C é a linguagem sucessora do B (não é meme), tendo sido criada pelos mesmos pesquisadores: [Ken Thompson](https://en.wikipedia.org/wiki/Ken_Thompson) e [Dennis Ritchie](https://en.wikipedia.org/wiki/Dennis_Ritchie). Feita no lendário Bell Labs, sua origem está inextricavelmente ligada ao [UNIX](https://pt.wikipedia.org/wiki/Unix). Tão simples que cabe em um livro (relativamente) curto: [The C programming language](https://www.cimat.mx/ciencia_para_jovenes/bachillerato/libros/%5BKernighan-Ritchie%5DThe_C_Programming_Language.pdf). Tão poderosa que escreveu os sistemas operacionais mais importantes que já existiram.

Ela surgiu no início dos anos 70, a partir da tentativa de Ritchie de melhorar a linguagem B, que havia sido inventada para a escrita do sistema operacional Unix. Após poucos anos de desenvolvimento, em 1973, C já tinha um pré-processador e estava relativamente madura, tanto que foi utilizada para reimplementar o kernel do Unix.

Uma década depois, C havia se tornado bastante popular, o que levou a ANSI a produzir documentos padronizando a especificação da linguagem. Em 1989 este padrão foi ratificado pela ANSI, recebendo o nome de C89. No ano seguinte, ele foi adotado pela ISO, recebendo o novo nome de C90 (mas que se refere à mesma especificação que o C89). Desde então, muitas outras adições foram feitas à linguagem C, sendo a versão mais recente o C23. Contudo, hoje em dia a maioria das aplicações são escritas ou com C99 ou com C17.

Caso queira conhecer mais sobre o C moderno, o livro "Effective C, 2nd Ed" é um ótimo complemento, com o autor sendo um dos membros do comitê da ISO para padronização do C. Também temos o [Modern C](https://inria.hal.science/hal-02383654v2/file/modernC.pdf), disponível legalmente na íntegra no site.

## Características importantes do C

### Característica 1 - "Baixo" Nível

Em nosso dia a dia, o termo _baixo nível_ costuma ter um caráter um tanto prejorativo. Por exemplo, um atleta que está tendo uma performânce de **baixo** nível está se saindo pior do que um adversário que está tendo uma parformânce de **alto** nível. Um jogador que está em um nível baixo em um jogo, é pior ou menos experiente do que um jogador que está em um nível alto.

No contexto das linguagens de programação, no entanto, "baixo nível" e "alto nível" são termos que não carregam por si só um juízo de valor. Estes termos dizem respeito ao quão abstraída é a linguagem em relação ao código de máquina, ou ao quão próxima a linguagem está de interagir diretamente com o hardware de uma máquina. Tentando definir melhor os termos, podemos dizer que:

- **Linguagem de baixo nível**: é uma linguagem que não possui muitas camadas de abstração ou funcionalidades facilitadoras para os programadores. Ao escrever código em uma linguagem de baixo nível, você precisa estar ciente de muitos detalhes sobre a arquitetura e o funcionamento do hardware. Além disso, a sintaxe de uma linguagem dessas costuma ser mais "crua", o que você escreve reflete muito diretamente o que acontecerá de fato no processador da máquina.
- **Linguagem de alto nível**: é o tipo de linguagem que foi feita em cima de algumas camadas de abstração das linguagens de baixo nível. Linguagens de alto nível geralmente possuem sintaxes um tanto mais elaboradas, e que te permitem fazer com meia dúzia de linhas de código o que antes seria feito com 200 linhas.

Essas duas categorias não representam uma realidade dual e absoluta. As linguagens não pertencem a _uma_ das duas categorias e acabou, na verdade estes termos representam os extremos de um **espectro**. Por isso no título desta subseção a palavra "baixo", em "baixo nível", está entre aspas - pois C não é totalmente baixo nível, mas também não chega a ser abstraída o suficiente para a maioria das pessoas considerá-la alto nível.

Tentando fazer uma analogia aqui, programar em uma linguagem de baixo nível é como costurar com uma agulha, enquanto programar em alto nível é como usar uma máquina de costura. Usando uma agulha, você possui grande controle sobre todos os detalhes do fiar de um suéter, mas o processo será demorado e você precisará ser brabo na costura, ou o resultado ficará uma aberração. Usando uma máquina de costura, seu controle será menor, mas o processo será rápido e sua habilidade com uma agulha não será tão relevante. Note que nesta analogia, o tempo de costurar o suéter não é o tempo de execução de um programa, e sim o tempo de escrever o código em si. Na verdade, o tempo de execução de programas escritos em linguagens de baixo nível (agulhas) é via de regra bem menor do que o tempo de execução de programas escritos em linguagens de alto nível. Ou seja, por estarem mais próximas do hardware e da linguagem de máquina, códigos de baixo nível costumam ser mais eficientes do que sua contra-parte.

### Característica 2 - Sintaxe simples

Apesar de ser uma linguagem de baixo nível, C possui uma sintaxe surpreendentemente legível para humanos. Isto se deve principalmente por seu minimalismo, já que ele originalmente possui apenas [32 palavras-chave](https://en.wikipedia.org/wiki/C_(programming_language)#Reserved_words).

Comparando com [línguas artificiais](https://pt.wikipedia.org/wiki/L%C3%ADngua_artificial), C está mais para um [Toki Pona](https://tokipona.org/) do que para um [Esperanto](https://pt.wikipedia.org/wiki/Esperanto). Isto não significa que todo programa em C será fácil de ler, significa apenas que se você escrever em C igual um ser humano, conseguirá fazer coisas complexas com ferramentas relativamente simples.

### Característica 3 - Compilada

De forma super simplificada, linguagens costumam cair em uma de duas caixas: compiladas ou interpretadas. Aqui vai uma leve definição das duas.

- **Compilada**: Programas feitos com linguagens compiladas basicamente precisam ser transformados em um arquivo executável antes de rodarem. O processo de transformar código fonte (texto escrito na linguagem de programação) em linguagem de máquina (`0` e `1`) é o que chamamos de compilação, e ele é feito por um... compilador o_o. Neste processo de compilação há várias etapas, incluindo a detecção de erros que podem ser conferidos analisando-se o próprio código.
- **Interpretada**: linguagens interpretadas têm seu código analisado e transformado em código de máquina durante a própria execução. Ou seja, um interpretador é basicamente um "compilador em tempo real". Por conta desta característica, certos tipos de erro não podem ser detectados de antemão, e provavelmente causarão crashes durante a execução do programa. Exemplos de linguagens interpretadas são o JavaScript e o Lua.

Como é de costume, ambos os tipos de linguagem possuem suas vantagens e desvantagens. Linguagens compiladas não precisam se preocupar com traduzir o código durante a execução, então costumam ser mais rápidas. Por outro lado, tempos de compilação podem ser bem altos para projetos grandes e se tornar um incômodo no ciclo de desenvolvimento, o que simplesmente não é um problema para linguagens interpretadas. Há também uma questão de portabilidade, pois programas compilados só podem rodar para a arquitetura de processador para a qual eles foram compilados, enquanto um programa interpretado pode rodar em qualquer máquina que tenha o interpretador da linguagem instalado. Por conta de tudo isso, há linguagens que tentam combinar aspectos de ambas as abordagens para obter um resultado mais equilibrado, como o Java e o Python, que compilam seus códigos para uma linguagem intermediária (bytecode) e então usam interpretadores nesta linguagem com suas máquinas virtuais (JVM e PVM, respectivamente).

### Característica 4 - Tipagem estática e fraca

Nós sequer explicamos o que é tipagem ou o que são variáveis ainda, então você vai ter que confiar um pouco no que eu vou dizer agora sem muito contexto. 

> Se você conseguir lembrar, revisite esta seção depois de ler o próximo capítulo.

A programação - e a computação no geral - pode ser resumida como _manipulação de valores_. Aí que vem a bomba: **valores possuem TIPOS**. Se você já viu um aparato computadorizado, você provavelmente consegue imaginar ele fazendo contas. O que é uma conta? é manipulação de **números** (guarde isso). Você também deve conseguir imaginar um computador manipulando **texto**, o meu por exemplo está fazendo isto enquanto escrevo este parágrafo. Qual é a diferença entre a manipulação de números e a manipulação de textos? Na verdade os dois são bem semelhantes, mas podem possuir algumas diferenças chave. Ao programar, nós precisamos ser capazes de distinguir quais valores são números e quais valores são textos, para que nosso computador lide com eles da forma correta. Dito isso, "número" e "texto" são TIPOS de valores. 

Praticamente toda linguagem de programação possui um sistema de tipos, ou seja, um conjunto de tipos aos quais os valores (variáveis) podem pertencer. Este sistema de tipos é o que chamamos de _tipagem_. Agora podemos finalmente chegar no ponto que importa: C possui tipagem estática e fraca.

O sistema de tipos de uma linguagem de programação pode variar em dois eixos: DINÂMICA vs ESTÁTICA e FRACA vs FORTE. Aqui vão as definições:

- **Tipagem estática**: o tipo de todos os valores é conferido durante a compilação do programa. Caso alguma operação ou manipulação seja aplicada em um valor de tipo errado, o compilador dá chilique e te avisa que seu código não faz sentido. Além disso, valores não podem trocar de tipo durante a execução do programa.
- **Tipagem dinâmica**: os valores não possuem um tipo fixo; uma variável que representava um número pode passar a representar um texto por algum motivo. Sendo assim, o programa roda confiando que sua manipulação de valores faz sentido, e quando ele encontra algo que não faz, o mundo explode (na verdade só um erro é gerado, mas é quase a mesma coisa). A maioria das linguagens interpretadas possuem tipagem dinâmica.
- **Tipagem forte**: as variáveis de um tipo só podem ser convertidas para outro tipo de forma _explicita_. O programador deve dizer em voz alta com seu editor de texto aberto a seguinte frase: "eu permito que esta variável seja convertida para outro tipo!". Ok, não é bem assim, mas o programador deve usar uma sintaxe da linguagem para indicar onde uma conversão de tipos está ocorrendo.
- **Tipagem fraca**: os valores podem ser convertidos implicitamente, não é necessário falar com seu monitor e nem fazer específico. Contudo, isto pode acabar permitindo que você converta sem querer tipos que não são muito compatíveis, causando comportamentos indesejados (insetos!! quero dizer... bugs!!!!).

No C, o compilador confere a tipagem das variáveis para ter certeza de que você não está colocando um texto em uma caixa marcada com um adesivo escrito "caixa exclusiva para números inteiros". Contudo, ele deixa que você, sem dizer nada, troque o adesivo (temporariamente) para um que diz "caixa exclusiva para números reais", o que configura uma conversão de tipos implícita.

### Característica 5 - Procedural

Existe uma coisa muito engraçada (mentira inofensiva) chamada "Paradigmas de Programação". Paradigmas são basicamente formas e filosofias distintas de se escrever código. O que acontece é que não é exatamente você, humano, que escolhe qual paradigma você seguirá ao programar. A maioria das linguagens possui uma sintaxe e funcionalidades que te levam a seguir um paradigma específico. Você pode até tentar dar uma forçada e programar em um paradigma que não é o padrão daquela linguagem, mas no geral é melhor agir em conformidade com as autoridades.

Os paradigmas mais populares e comuns, juntamente com suas características principais, estão listados abaixo:

- **Procedural**: primeiramente o que se aplica ao C. O paradigma procedural é um subset do paradigma imperativo. O paradigma imperativo se consiste na ideia de que você escreve um código que diz _como_ as coisas são feitas, e não _o que_ deve ser feito. Isto pode soar bem confuso (por muito tempo soou para mim também), mas é parte do processo. Basicamente, o código imperativo foca em explicar os passos do processo para se chegar a um resultado, incluindo uma manipulação clara do fluxo de controle e da mudança de estados. Já sua contra-parte, o paradigma **declarativo**, foca na definição do resultado em si. O paradigma procedural é um paradigma imperativo somado à organização do código em funções (procedimentos) que utilizam uns aos outros.
- **Orientação a Objetos**: introduz o conceito de um "objeto" e de uma "classe" para tentar representar totalidades mereológicas (como gatinhos, carros ou pessoas) de forma útil. Desde sua origem nos anos 60, a orientação a objetos se tornou um tópico relativamente profundo, com linguagens extremamente populares aderindo fortemente às suas ideias, como o Java, o C++ e o C#.
- **Funcional**: possuindo raízes mais acadêmicas e matemáticas (no _cálculo lambda_ e _teoria das categorias_), o paradigma funcional faz parte da família de paradigmas _declarativos_. A proposta principal deste tipo de programação é utilizar apenas _funções puras_, que são funções determinísticas e que não produzem efeitos colaterais, como mudanças de estado.
- **Lógica**: Também faz parte dos paradigmas _declarativos_. Seu funcionamento é semelhante à lógica proposicional. A ideia é que o programador defina _fatos_ e _regras_ sobre o universo do problema, e com base nestes fatos e regras é possível fazer "perguntas" ao universo para se obter respostas automaticamente.

Apesar de haver muito debate sobre qual é o melhor paradigma de programação, no fim do dia cada um tem o seu propósito... ~dito isso, o paradigma funcional é o mais irado~

## Conclusão

Dennis Ritchie é muitas vezes chamado de "o pai das linguagens de programação". Isto ocorre por bons motivos, pois sua criação - o C - se destaca de muitas formas:

- Ele é elegante e poderoso;
- Surgiu em um momento chave na história da computação;
- Influenciou o design da maioria (se não todas) as linguagens que vieram depois dele;
- Foi usado para o desenvolvimento de inúmeros softwares lendários;

Apesar de velho, o C ainda é muito utilizado hoje em dia, além de ser amplamente considerada uma boa primeira linguagem de programação para se aprender. Isto nos trás ao aqui e agora... A partir de agora, nesta trilha, iremos aprender de fato a programar em C. Espero que você esteja animado para entender, pois eu sei que estou animado para ensinar!

Até o próximo capítulo :)
