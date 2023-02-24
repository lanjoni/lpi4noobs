# Shell Script

Já parou pra pensar em como seria interessante juntar todos os comandos aprendidos até o momento em um único script, sendo capaz de executar determinada tarefa da maneira como desejar? Pois é, dessa visão surgiu o que chamamos de "Shell Script"!

Shell Script é o nome dado a todo script escrito para ser interpretado por um interpretador de shell, utilizando comandos, variávies e diversas funcionalidades que podem ser aplicadas de acordo com a vontade do programador!

## Estrutura

Normalmente a extensão utilizada para arquivos em shell script é a extensão ".sh", mas, como já estudamos, no Linux você não precisa necessariamente de uma extensão no arquivo para interpretar e salvar ele, basta indicar quem vai realizar tais tarefas, por isso, vamos criar um novo arquivo de shell script a ser executado utilizando o comando touch:

```sh
$ touch teste.sh
```
> Para editar este arquivo utilize o editor de sua preferência, podendo ser o VIM, Emacs, ou o que desejar.

O primeiro ponto a se destacar: comentários. Nos arquivos de shell script utilizamos a cerquilha ("#") para inserir comentários em determinadas linhas, na qual a primeira linha de nosso script começa com um comentário responsável por indicar qual vai ser o interpretador de shell a ser utilizado durante a interpretação de nosso script. A indicação de qual será o interpretador não é necessária toda vez, mas, nos casos em que não for indicado, será utilizado o interpretador padrão.

Na primeira linha vamos adicionar:

```sh
#!/bin/bash
```
> "/bin/bash" é o caminho de nosso shell padrão, mas, caso queira utilizar outro, basta alterar para o caminho (de preferência absoluto) para o interpretador que desejar.

Certo, agora vamos imprimir nossa primeira mensagem: um simples e claro "Hello World!". Para isto veja como ficou nosso exemplo abaixo:

```sh
#!/bin/bash

echo "Hello World!"
```
> "echo" é o comando utilizado para imprimir alguma mensagem!

Agora com nosso primeiro shell script pronto, após salvar nosso arquivo, vamos executar simplesmente chamando pelo arquivo, podendo se utilizar o caminho aabsoluto ou caminho relativo.

### Caminho absoluto

```sh
$ /caminho/para/teste.sh
```
> Com o caminho começando da raíz do sistema operacional.

### Caminho relativo

```sh
$ ./teste.sh
```
> Imaginando que já estamos no diretório do próprio arquivo.

Perceba que não aconteceu nada, correto? Um erro de execução! O motivo é simples: não temos permissão para executar o arquivo! Este foi um tópico abordado anteriormente quando falamos sobre permissionamento! 

Para adicionar permissão de execução para **todos** os usuários basta utilizar o comando:

```sh
$ chmod +x teste.sh
```

Assim, podemos ver as permissões com o comando `ls -l` para uma listagem detalhada! Agora podemos já executar nosso shell script e pronto! Tudo funcionará perfeitamente!

## Variáveis

A definição de variáveis também é bem simples: basta escrever o nome da sua variável e igualar ao valor desejado, **sem espaços**. Para "chamar" esta variável em algum local basta utilizar o nome da variável com um sinal de cifrão ("$") no começo.

Veja um exemplo abaixo de criação e uso de variável:

```sh
#!/bin/bash

nome="guto"

echo "Oi $nome"
```
> As aspas duplas permitem a invocação de variáveis em seu conteúdo, enquando as aspas simples não.

