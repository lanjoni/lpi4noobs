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

As letras de definição são:
- **u** = usuário
- **g** = grupo
- **o** = outros

## Definindo permissões com valores numéricos

Uma outra forma de definir permissões é utilizando números, assim, conseguimos definir com uma linha de três números quais serão as permissões para cada arquivo. Um exemplo de tabela poderá mostrar como é feita a lógica por trás desse permissionamento:

| Permissão | Binário | Decimal |
|-----------|---------|---------|
| ---       | 000     | 0       |
| --x       | 001     | 1       |
| -w-       | 010     | 2       |
| -wx       | 011     | 3       |
| r--       | 100     | 4       |
| r-x       | 101     | 5       |
| rw-       | 110     | 6       |
| rwx       | 111     | 7       |

O que esse monte de números quer dizer? Bom, os valores decimais vão definir quais serão suas permissões para usuário, grupo e outros, mas, para entender melhor como funciona este modelo veja que:

- **r** vale 4
- **w** vale 2
- **x** vale 1

Então, se eu quiser, por exemplo, definir as permissões de leitura, escrita e execução para meu usuário, apenas leitura para meu grupo, e nenhuma permissão para os outros eu utilizaria o comando:

```sh
$ chmod 740 teste.txt
```

Assim, teríamos a seguinte visualização de permissões quando utilizássemos o comando `ls -l`:

```sh
-rwxr-----
```

Mas, por que? Simples:
- Usuário recebe leitura + escrita + execução = 4 + 2 + 1 = 7
- Grupo recebe apenas leitura = 4
- Outros não recebem nada = 0

***O terrível 777***: tome muito cuidado! Como dizia o senhor tio Ben (tio do homem-aranha) "com grandes poderes vem grandes responsabilidades"! Definir "777" seria nada mais que permitir que todos podem fazer o que quiserem com seu arquivo! Esta falha pode ser gravíssima!

## Propriedade do arquivo

Já parou pra pensar que um arquivo criado por você possui propriedade inteiramente sua? Isso significa que todo comando `chmod` executado para usuário será para você mesmo! Mas, caso eu quisesse mudar a quem é o usuário dono do arquivo, seria possível? A resposta é **sim**! Simples e prático com o comando `chown`!

O comando `chown` tem o papel de alterar as propriedades de um arquivo, neste caso, pense como se realmente fosse a propriedade de residência ou algo do tipo, quem "tem poder" sobre aquele arquivo, ou seja, quem é o dono!

A estrutura do comando é simples:

```sh
$ chown usuário arquivo
```
> Neste caso vamos passar a propriedade do *arquivo* para o *usuário*!

Então, tecnicamente falando caso eu tivesse um arquivo de teste e quisesse mudar sua propriedade seria bem simples, basta eu executar o comando informando primeiro o nome do usuário que eu quero que passe a ser dono do arquivo seguido do nome do arquivo!

```sh
$ chown novouser teste.txt
```

Certo, mas, caso este novo user tenha dois grupos, `novouser` e `administracao`, e eu queira passar para o novo user com o grupo administração, seria possível? A resposta é: sim! Veja um exemplo abaixo:

```sh
$ chown novouser:administracao teste.txt
```
> Basicamente adicionamos os dois pontos para depois informar o nome do grupo a ser adicionado!

Caso queira apenas alterar o grupo, basta colocar apenas os dois pontos seguido do nome do grupo, veja:

```sh
$ chown :administracao teste.txt
```
> Assim vamos passar a propriedade para o grupo adminstração!

Certo, mas, se eu quiser alterar a permissão de um diretório, e consequentemente de todos os arquivos que estão nele (imagine que tenhamos diversos arquivos e sub-diretórios dentro dele), como fazemos? Simples: utilizando o parâmetro "-R" indicando que faremos uma chamada recursiva, vindo do último arquivo do diretório para o primeiro, até chegar no próprio diretório! Basicamente o comando vai primeiro mudar de todo o conteúdo do diretório para depois apenas mudar dele em si. Veja um exemplo:

```sh
$ chown -R novouser ./Novo
```
> Neste caso mudamos do diretório novo partindo de nossa localização atual, por isso vem o ponto (".") antes! Ainda iremos estudar sobre caminhos!

Bom, e caso eu queira copiar as permissões de um usuário ou grupo para outro arquivo, como eu poderia fazer? Simples! Veja um exemplo abaixo utilizando o parâmetro de **referência**:

```sh
$ chown --reference=teste.txt novoteste.txt
```
> Neste caso a cópia de permissionamento é tanto para a propriedade quanto para as permissões em ci de leitura, escrita e execução para o próprio usuário, grupo(s) que pertence e outros!

## Permissões especiais

Determinadas ocasiões necessitam de determinadas permissões (até rimou). Este é um fato. Por isso vamos visualizar aqui três tipos de permissões especiais para nossos arquivos: *SUID* (**S**et owner **U**ser **ID**), *SGID* (**S**et **G**roup **ID**) e *Sticky bit*.

### SUID
O *SUID* tem como finalidade entregar uma permissão temporária para um usuário executar/utilizar um programa/arquivo com as permissões do proprietário do arquivo (nestes casos, geralmente este usuário proprietário é o superusuário root). **Somente** neste arquivo. Esta possibilidade permite que não haja necessidade de abrir o arquivo para acesso ou alterar sua propriedade.

Mas, já existe algum exemplo de aplicação que faz uso do SUID? Claro! Um exemplo é o comando `passwd`, utilizado para permitir que o usuário mude a própria senha: a mudança de senha realiza modificações no diretório "/etc/shadow", no qual apenas o superusuário root tem essa permissão! Mas, o usuário, obviamente, pode mudar sua própria senha. 

Certo, mas, como sabemos que o usuário possui o SUID ativado? Afinal, o SUID conta com um bit de ativação... Simples! Utilizando o comando `ls -l` já devemos visualizar uma substituição na posição de permissão para execução do usuário (no caso o "x"), sendo trocado por uma letra "s"! Se o "s" for minúsculo então o usuário tem permissão e se aparecer com o "S" maiúsculo significa que não possui permissão.

Um exemplo seria:

```sh
-rwsr-xr-x user teste.txt
```

Para habilitar o SUID é simples: basta adicionar o dígito "4" antes de seu início de permissões com o comando "chmod" utilizando os números decimais. Um exemplo seria:

```
# chmod 4750 teste.txt
```
> Para remover o bit SUID basta trocar o "4" do início por "0".

**Curiosidade**: caso você queira visualizar quais arquivos no seu sistema possuem o bit SUID ativo, basta executar o seguinte comando: `find / -perm +4000`. Para visualizar um comando que mostra o "s" basta executar o comando `ls -l /caminho/do/comando`, neste caso, poderia ser `ls -l /bin/ping`.

### SGID

A única diferença entre o SUID é que ao invés de executar o arquivo com as permissões de dono será executado com as permissões de grupo do arquivo. Ao invés da letra "s" aparecer nas permissões de execução do usuário, aparecerá nas permissões de execução do grupo, sendo algo parecido com o exemplo:

```sh
-rwxr-sr-x user teste.txt
```
> Lembrando que o "s" minúsculo indica que possui permissão de execução do grupo e o "S" maiúsculo indica que não possui permissão.

Para habilitar o SGID ao invés de utilizarmos o número "4" utilizaremos o número "2" no início de nossas permissões, assim como no exemplo abaixo:

```
# chmod 2750 teste.txt
```
> Para remover o bit SGID basta trocar o "2" do início por "0".

**Curiosidade**: caso você queira visualizar quais arquivos no seu sistema possuem o bit SGID ativo, basta executar o seguinte comando: `find / -perm +2000`. Para visualizar um comando que mostra o "s" basta executar o comando `ls -l /caminho/do/comando`.

**Atenção**: cuidado ao trabalhar com as permissões especiais, afinal, qualquer execução será feita com privilégios do usuário dono do determinado arquivo (podendo muita das vezes ser o superusuário root)! Isto significa que caso seu arquivo inicie uma nova sessão um subshell (como com algum editor de texto via terminal), será iniciada como superusuário root.

### Sticky bit

Utilizado para impossibilitar que os demais usuários possam excluir os conteúdos de diretórios, mesmo que ainda haja a permissão de escrita no diretório. Isto significa que um usuário poderia ter um diretório na qual pode editar arquivos, enviar novos arquivos, salvar novos arquivos, mas, nunca excluir. Somente o proprietário do arquivo e o superusuário root possuem permissão para excluir arquivos neste diretório.

Ao invés da letra "s" teremos a letra "t", na qual o "t" minúsculo indica que possui permissão de execução e o "T" maiúsculo indica que não possui permissão. A letra ficará na última posição, no mesmo campo responsável por indicar a permissão de execução para outros. Observe o exemplo abaixo:

```sh
-rwxr-xrwt user Novo
```

Para habilitar o Sticky bit ao invés de utilizarmos o número "4" ou "2", utilizaremos o número "1"  no início das permissões com o chmod. Um exemplo seria:

```
# chmod 1757 teste.txt
```

**Curiosidade**: caso você queira visualizar quais arquivos no seu sistema possuem o Sticky bit ativo, basta executar o seguinte comando: `find / -perm +1000`. Para visualizar um comando que mostra o "s" basta executar o comando `ls -l /caminho/do/comando`.

---

Muito bom! Estou orgulhoso de você ter chego até aqui! O que achou do funcionamento do permissionamento? Agora vamos para algumas atividades práticas e manipulações utilizando o nosso adorável interpretador de shell!

<p align="right">
  <a href="https://github.com/lanjoni/lpi4noobs/blob/main/content/pratica">Próximo -> Prática</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/lpi4noobs#roadmap">Voltar para o menu principal</a>
</p>
