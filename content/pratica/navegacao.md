# Navegação

Navegar entre diretórios utilizando o terminal é uma tarefa que você vai realizar com bastante frequência, por isso, surge a necessidade de entender como funciona todo este processo, para que assim você consiga utilizar o terminal de uma forma única e incrível, com total integração e velocidade.

Antes de partir para os comandos precisamos entender como eles funcionam e como a "sua localização" pode influenciar em tudo isso, assim, entenderemos primeiramente o que são caminhos e como eles se comportam!

## O que é um caminho?

Um caminho nada mais é que a "sequência de diretórios abertos para se localizar um determinado arquivo", na qual, basicamente falando, podemos dizer que o caminho é onde um arquivo pode ser encontrado, além de determinar quais tipos de arquivos podemos ter nos diretórios em questão (por isso tivemos que entender a estrutura de diretórios primeiro).

Quando você abrir seu terminal e inicializar seu interpretador de shell, provavelmente você estará no diretório "home" de seu usuário! Para verificar em qual diretório você está basta utilizar o comando `pwd`.

### PWD

```sh
guto@turing:~$ pwd
/home/guto
```

O retorno "/home/guto" significa que eu estou no diretório home de meu usuário, mas, no seu caso aparecerá com seu nome obviamente. Este retorno nada mais é do que o caminho em que estou.

A importância de sabermos o diretório em que estamos localizados é essencial para os próximos comandos que vamos apresentar!

## Caminho relativo

Quando falamos em caminho temos que separar em duas vertentes: caminho absoluto e caminho relativo. O caminho relativo é todo caminho partindo do diretório em que eu me encontro. Neste caso vamos realizar uma tarefa simples: entrar no diretório de "Downloads", criar um novo diretório, entrar neste diretório e voltar para o diretório home do meu usuário apenas utilizando caminhos relativos! Vamos lá?

### CD

Após abrir seu terminal utilize o comando `cd` para entrar em algum diretório, assim, entraremos no diretório de Downloads:

```sh
guto@turing:~$ cd Downloads
/home/guto/Downloads
guto@turing:~/Downloads$
```

### MKDIR

Ótimo! Agora estamos em nosso diretório de Downloads do meu usuário. Agora, vamos criar um novo diretório chamado "Novo" e entraremos neste subdiretório de Downloads:

```sh
guto@turing:~/Downloads$ mkdir Novo
guto@turing:~/Downloads$ cd Novo
guto@turing:~/Downloads/Novo$
```

Excelente! Agora que já entramos neste novo diretório vamos voltar para o diretório home de nosso usuário utilizando o caminho relativo:

```sh
guto@turing:~/Downloads/Novo$ cd ../..
guto@turing:~$
```
> Os dois pontos `..` simbolizam que queremos ir para o diretório anterior! Utilizar da forma que utilizamos significa que voltamos para dois diretórios anteriores!

## Caminho absoluto

Agora que já entendemos como é o funcionamento do caminho relativo (partindo do ponto em que eu me encontro), vamos entender o que é o caminho absoluto: o caminho geral, absoluto, partindo desde a raíz de nosso sistema operacional e direcionando para o diretório em questão.

Um exemplo prático seria ao invés de utilizarmos o comando `cd Downloads/Novo` partindo do diretório home de nosso usuário, utilizar `cd /home/guto/Downloads/Novo` e iríamos obter o mesmo resultado!

Basicamente falando o caminho absoluto sempre vai começar com esta barra "/" no começo, pois significa que estamos partindo da raiz de nosso sistema operacional!

O uso de cada um vai depender da localização em que seu usuário estiver, afinal, em diversas ocasiões utilizar o caminho relativo não será a melhor forma!

## Home

Um truque interessante é: a home do usuário logado sempre será representada pelo sinal de um "til" (~), isto significa que aquele sinal no começo não era besteira, mas, o sinal do "til" seria equivalente ao diretório "/home/guto"!

Certo, então quer dizer que se eu utilizar o comando `cd ~` eu irei voltar para a home de meu usuário? Sim! Digo ainda mais: se você utilizar o comando `cd` apenas sem nenhuma adição ele vai te enviar diretamente para o home de seu usuário (dependendo do seu interpretador de shell)!

## . e ..

Enquanto `..` significa o diretório anterior, você sabia que o `.` significa o diretório atual? Isto é: se você estiver no home de seu usuário e quiser entrar no diretório de Downloads, uma outra forma seria adicionar um `./` antes do nome! Veja:

```sh
guto@turing:~$ cd ./Downloads
/home/guto/Downloads
guto@turing:~/Downloads$ 
```

---

Ótimo! Agora que você sabe como navegar entre diretórios o que acha de aprender a manipular arquivos?

<p align="right">
  <a href="https://github.com/lanjoni/lpi4noobs/blob/main/content/pratica/manipulacao.md">Próximo -> Manipulação</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/lpi4noobs#roadmap">Voltar para o menu principal</a>
</p>
