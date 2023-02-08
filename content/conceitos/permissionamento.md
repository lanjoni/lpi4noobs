# Permissionamento

Para entender melhor sobre o funcionamento do permissionamento irei exemplificar com uma prática em minha parte em um ambiente separado que preparei. Caso queira preparar um ambiente, basta definir um diretório para criar seus arquivos de teste e criar **um diretório** e **um arquivo de texto comum**. Para isso via terminal execute os seguintes comandos (que ainda vamos discutir posteriormente sobre):

```sh
$ mkdir Novo && touch teste.txt
```

## Compreendendo o permissionamento

Podemos definir o permissionamento como o ato de definir restrições sobre o uso de algum arquivo ou diretório para determinados usuários. Como falado anteriormente, o superusuário root tem permissão para qualquer uso, independente de demais restrições, por isso, mantenha utilizando seu usuário comum durante este tópico.

O permissionamento está presente em todos os sistemas baseados em Unix, por isso sistemas operacionais Unix-like como macOS, FreeBSD, OpenBSD e outros, terão compatibilidade com estes mesmos conceitos.

A primeira coisa a se fazer é executar o comando `ls -l` em seu diretório para listar os arquivos de forma detalhada, assim, você terá um retorno parecido com isso:

```sh
drwxr-xr-x 2 user user 4096 Feb 8 18:30 Novo
-rw-r--r-- 1 user user    0 Feb 8 18:30 teste.txt
```
> Os dados que provavelmente estarão diferentes serão a data de criação, hora de criação e nome do usuário.

Vamos focar nos primeiros caracteres que vem antes dos números, que neste caso são:

```sh
drwxr-xr-x
-rw-r--r--
```

A primeira letra significa o tipo de arquivo com que estamos lidando. Os arquivos podem ser dos ser visualizados dos seguintes tipos e definição de caracteres:
- d: diretório
- b: arquivo de bloco
- c: arquivo especial de caractere
- p: canal
- s: socket
- l: link simbólico (famoso "atalho")
- -: arquivo "normal"

Ou seja, seguindo as definições acima, temos um diretório e um arquivo "comum"! 

## Diferenciação de permissões

Vamos focar no primeiro item listado: o diretório. Vamos colar abaixo como ficou sua sequência de caracteres:

```sh
drwxr-xr-x
```

Primeira letra (***d***): determinação de qual tipo de arquivo estamos lidando, neste caso, um diretório.

Segunda, terceira e quarta letra (***rwx***): Mostra as permissões do proprietário do arquivo, neste caso, o chamado "user".

Quinta, sexta e sétima letra (***r-x***): Mostra as permissões do(s) grupo(s) que o usuário pertence.

Oitava, nona e décima letra (***r-x***): Mostra as permissões para os demais usuários.

Mas afinal, o que significam estas letras?

- **r** = Permissão para leitura (***r**ead*)
- **w** = Permissão para escrita (***w**rite*)
- **x** = Permissão para execução (*e**x**ecution*)
- **-** = Sem permissão

No exemplo acima do diretório podemos dizer que:
- O usuário tem permissão para leitura, escrita e execução do diretório;
- Os grupos que o usuário pertence tem permissão para leitura e execução apenas;
- Os demais usuários tem permissão para leitura e execução apenas;

## Atribuição de permissões

Existem duas principais formas para definir e alterar permissões com o comando `chmod`. A primeira que vou apresentar é escrevendo por extenso as permissões. Para um exemplo prático vamos utilizar o arquivo "teste.txt" criado anteriormente, que possui atualmente a seguinte configuração de permissões:

```sh
-rw-r--r--
```

Vamos primeiramente adicionar uma permissão de execução para o usuário utilizando o comando `chmod`, para isso utilize:

```sh
$ chmod u+x teste.txt
```
> A sintaxe respeita *caractere correspondente para usuário, grupo ou outros + caracter de permissões a se adicionar*

Utilizando o comando `ls -l` veremos agora suas permissões como:

```sh
-rwxr--r--
```

Agora eu quero adicionar permissão de escrita e execução para os grupos dos quais o usuário pertence, para isso vamos utilizar o seguinte comando:

```sh
$ chmod g+wx teste.txt
```

Agora com o comando `ls -l` veremos uma resposta de permissionamento como:

```sh
-rwxrwxr--
```

Certo, agora eu quero deixar os outros apenas com permissão de execução do arquivo, sem permissões de leitura e escrita:

```sh
$ chmod o=x teste.txt
```
> Ao invés do sinal de adição (+) utilizamos o sinal "de igual" (=) para definir **todas** as permissões que deverá ter, neste caso, os "outros" (demais usuários)

Assim, a resposta para o permissionamento será algo como:

```sh
-rwxrwx--x
```

Desta forma: 
- Nosso usuário tem permissão de leitura, escrita e exeução; 
- Os grupos que o usuário pertence possuem permissão para leitura, escrita e execução; 
- Os demais usuários tem permissão de execuçao apenas;

As letras
