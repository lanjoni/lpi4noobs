# Manipulação de arquivos

A manipulação de arquivos é outra tarefa que, com toda certeza, você vai utilizar muito, seja para copiar, remover, criar e até mover arquivos. Todas estas funcionalidades serão abordadas neste tópico, por isso, abra seu diretório para testes e vamos para a prática!

## Touch

O comando `touch` é utilizado para criar novos arquivos em branco, por isso, vamos criar três novos arquivos e depois visualizar cada um deles listando o conteúdo de nosso diretório! Veja:

```sh
guto@turing:~$ touch novo1.txt
guto@turing:~$ touch novo2.txt
guto@turing:~$ touch novo3.txt
guto@turing:~$ ls
novo1.txt  novo2.txt  novo3.txt
```

## Cat

O comando `cat` é utilizado para visualizar o conteúdo de um arquivo, sendo muito útil quando precisamos visualizar um conteúdo simples de algum arquivo! Seu uso é bem simples, basta utilizar a estrutura `cat nomedoseuarquivo` e ele irá imprimir no nosso terminal o conteúdo! Um detalhe importante é que como não escrevemos nada dentro destes arquivos seu resultado será em branco! Mas calma, fique tranquilo! Para testar você pode criar a parte um arquivo novo e editar utilizando o "gedit" com interface gráfica, além de utilizar algum editor de texto em terminal (que ainda veremos em breve)!

## Head e Tail

O comando cat pode ser não tão útil certo? Afinal, nem sempre queremos ver todo o conteúdo do arquivo... Talvez precisemos ver apenas o começo ou final de um documento... Para isso temos o comando `head` que mostra as 10 primeiras linhas de um arquivo, além do comando `tail` que mostra as dez últimas! 

Você ainda pode definir a quantidade de linhas a serem visualizadas com o parâmetro "-n numero" trocando a palavra para a quantidade de linhas que deseja visualizar!

Um exemplo prático para mostrar as cinco primeiras linhas seria:

```sh
guto@turing:~$ head -n 5 novo.txt
```

Um detalhe importante é que traduzindo do inglês "head" significa "cabeça" e "tail" significa "cauda", ou seja, seria como se o "comando head mostra apenas a cabeça de um arquivo enquanto o comando tail mostra apenas a cauda". Legal não? Mais legal ainda é pensar que "cat" mostra o documento todo e que na realidade "todo documento seria um gato"... 😲

## Cp

Copiar arquivos é uma tarefa que fazemos diariamente correto? Para isso existe o comando `cp`, utilizado para realizar cópias de arquivos com uma estrutura simples: `cp *diretório do arquivo que quer copiar* *diretório para onde quer enviar*`! Na prática seria algo como o exemplo abaixo:

```sh
guto@turing:~$ cp novo.txt ../
guto@turing:~$ cp novo.txt /usr/bin
guto@turing:~$ cp /usr/bin/novo2.txt . 
```
> O ponto único "." indica o diretório atual, enquanto os dois pontos ".." indicam o diretório anterior.

Para copiar diretórios utilizamos a mesma estrutura, mas, com um detalhe: diretórios possuem conteúdo dentro, por isso, há a necessidade de utilizarmos o parâmetro `-r` indicando ser uma cópia recursiva, afinal, além do diretório precisamos copiar todo o seu conteúdo! Um exemplo prático seria:

```sh
guto@turing:~$ cp -r /home/user2 .
```

Mas e se eu quisesse todo o conteúdo do diretório, mas, sem copiar ele? Simples: 

```sh
guto@turing:~$ cp -r /home/user2/* .
```
> O sinal de asterisco "`*`" indica que queremos todo o conteúdo de um diretório, sem restrições! Este sinal se refere à todos os arquivos, mas, em breve vamos descobrir como podemos definir parâmetros para esta seleção!

## Mv

O comando `mv` é utilizado para mover arquivos, além de ter uma função bem específica: renomear arquivos. O ato de renomear um arquivo é feito com o comando "mv", afinal, estamos movendo um arquivo para o mesmo diretório em que se encontra, mas, alterando seu nome! Sua estrutura é idêntica ao comando "cp", mas, com um detalhe bem importante a ser tratado, por isso, veja o exemplo abaixo.

```sh
guto@turing:~$ mv novo.txt novo4.txt # Renomeando o arquivo
guto@turing:~$ mv novo.txt ../ # Movendo o arquivo para o diretório anterior
guto@turing:~$ mv novo.txt ../novo4.txt # Movendo o arquivo para o diretório anterior e renomeando ele
```

## Rm e rmdir

Ambos os comandos possuem função de remover arquivos, mas, enquanto o comando `rm` remove arquivos, o comando `rmdir` remove diretórios **vazios**! O `rm` ainda pode ser utilizado em diretórios com o parâmetro `-r` (assim como com o comando "cp") para indicar uma remoção recursiva, por isso, vamos ver alguns exemplos:

```sh
# rm
guto@turing:~$ rm novo.txt
guto@turing:~$ rm -r Novo # Este é um diretório não vazio!

# rmdir
guto@turing:~$ rmdir NovoVazio # Este é um diretório vazio!
```
