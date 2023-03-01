# Usuários

A administração de usuários dentro de um sistema operacional Linux é uma tarefa importante, afinal, o Unix em seu lançamento fez muito sucesso pela possibilidade de trabalhar com mais de um usuário simultaneamente, por isso, entender como podemos gerenciar usuários no nosso sistema operacional é algo essencial!

## Adicionando usuários

Para adicionar um usuário é bem simples, mas precisamos definir alguns parâmetros para que essa adição seja feita de forma correta, por isso, vamos conhecer algumas formas:

### Adicionando um usuário com um diretório "/home/nome_do_usuario" por padrão:

```
# useradd -m nome_do_usuario
```
> A opção `-m` é utilizada para criar automaticamente um diretório para este novo usuário no caminho partindo do "/home"!

### Adicionando um usuário com um diretório personalizado "home":

```
# useradd -m -d /caminho_do_home_novo nome_do_usuario
```
> Combinado com a opção `-d` conseguimos definir algum outro caminho para diretório padrão de home!

## Adicionando senhas para os usuários

Adicionar senhas para cada usuário criado é uma tarefa importante, afinal, com as senhas conseguimos garantir maior segurança sobre nossas ações! Veja como podemos adicionar uma senha para um usuário de forma simples:

```
# passwd nome_do_usuario
```

Automaticamente será necessário informar qual é a nova senha do usuário, lembrando que o usuário administrador "root" pode fazer o que quiser, afinal, tem permissões administrativas que garantem isso!

## Apagando usuários

Pode ser que por algum motivo específico você precise apagar algum usuário de seu sistema, por isso, basta utilizar o comando abaixo:

```
# userdel -r nome_do_usuario
```

Tome muito cuidado ao apagar usuários! Sempre veja e reveja o comando que está sendo executado com permissões administrativas!

## Criando um grupo

Com grupos podemos reunir diversos usuários que terão permissões compartilhadas entre si, seja para executar arquivos ou navegar entre diretórios! A criação de grupos é algo importante, e saber como gerenciar seus usuários entre estes grupos é essencial também. Mas, como eu consigo criar um grupo novo?

```
# addgroup nome_do_grupo
```

Assim que temos um grupo criado, podemos facilmente relecionar usuários que farão parte deste grupo, correto?

## Adicionando usuários em um grupo

Como dito anteriormente, existe a necessidade de termos permissões iguais para diferentes usuários em diferentes perspectivas, pois, garantimos segurança e confiabilidade de que as ações de cada usuário serão executadas como deveriam! Veja um exemplo abaixo para adicionar um usuário em algum grupo:

```
# usermod -a -G nome_do_grupo nome_do_usuario
```
> Um detalhe importante: se você utiliza o comando "sudo" ou então possui o "docker" instalado em sua máquina, por exemplo, você provavelmente faz parte de um grupo chamado "wheel" para que tenha acesso ao "sudo", além de um grupo chamado "docker" para acesso ao docker em si!

Diversas aplicações separam suas funcionalidades entre grupos de usuários, fazendo com que certas tarefas só possam ser executadas por determinados usuários, sendo esta separação de privilégios feita por grupos!

## Permissões para grupos

Como já estudamos no tópico de permissionamento, existem diversas formas para definir os privilégios que cada usuário terá em nosso sistema, valendo também para grupos, mas, existe um comando específico, definindo a propriedade de grupo em um diretório! Isto significa que todos os usuários daquele determinado grupo possuem acesso neste diretório. Veja um exemplo abaixo:

```
# setfacl -m g:operadores:rwx -R /caminho_de_diretorio
```
> Com este comando garantimos permissão para leitura (**r**), escrita (**w**) e execução (**x**) naquele diretório!

Assim, conseguimos manusear melhor as permissões de diretórios para nosso grupo!

## Apagando grupos

Talvez, por algum motivo específico, você precise ainda apagar algum grupo, por isso, existe um comando bem simples para este uso, veja:

```
# groupdel nome_do_grupo
```

Assim, apagaremos o grupo de forma simples e direta!

Caso você queira estudar um pouco mais sobre como podemos gerenciar usuários dentro de nosso sistema operacional Linux, acesse a página do [E-tinet](https://e-tinet.com/linux/gerenciar-usuarios-linux/)!

