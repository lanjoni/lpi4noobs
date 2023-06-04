# Shell Script

Já parou pra pensar em como seria interessante juntar todos os comandos aprendidos até o momento em um único script, sendo capaz de executar determinada tarefa da maneira como desejar? Pois é, dessa visão surgiu o que chamamos de "Shell Script"!

Shell Script é o nome dado a todo script escrito para ser interpretado por um interpretador de shell, utilizando comandos, variáveis e diversas funcionalidades que podem ser aplicadas de acordo com a vontade do programador!

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

Agora com nosso primeiro shell script pronto, após salvar nosso arquivo, vamos executar simplesmente chamando pelo arquivo, podendo se utilizar o caminho absoluto ou caminho relativo.

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
> As aspas duplas permitem a invocação de variáveis em seu conteúdo, enquanto as aspas simples não.

Certo, e se eu estivesse esperando o usuário digitar o nome dele? Simples! Basta utilizar o comando `read`!

```sh
#!/bin/bash

echo "Digite seu nome: "
read nome

echo "Oi $nome"
```

## Manipulação de valores

Seria possível o resultado de algum comando ser igualado ao valor de uma variável? A resposta é: sim. Veja um exemplo abaixo:

```sh
#!/bin/bash

ls1=$(ls -l /)
ls2=`ls -a /`

echo -e "LS 1:\n$ls1\n\nLS 2:\n$ls2"
```
> Parâmetro "-e" utilizado para interpretar quebras de linha e "\n" seria uma quebra de linha.

Podemos utilizar tanto "$(comandos aqui)" quanto "``` `comandos aqui` ```" (crase)!

## Tomada de decisão com IF

As tomadas de decisão são bem comuns quando falamos de programação em si, afinal, quem nunca utilizou um comando chamado "if"? Sua importância é extrema, por isso, veja como é a estrutura de um simples "if" em shell script:

```sh
#!/bin/bash

echo "Informe o número 1: "
read n1
echo "Informe o número 2: "
read n2

if [ $n1 -gt $n2 ]; then
        echo "Número 1 é maior que o número 2!"
elif [ $n1 -eq $n2 ]; then
        echo "Número 1 é igual o número 2!"
else
        echo "Número 1 é menor que o número 2!"
fi
```

Primeiramente vamos pedir para o usuário informar dois números, logo depois começamos o comando "if" que respeita a estrutura `if [ condição ]; then` (sendo essencial este ponto e vírgula além deste espaço entre os colchetes), seguido do comando "elif" que seria nada mais que o "else if" que estamos habituados, finalizando com um "else" e um "fi" para indicar a finalização da estrutura deste "if".

Percebeu que não utilizei símbolos nas comparações, mas, letras que se parecem com parâmetros? Pois é, desta forma comparamos valores em shell script!

### Lista de "símbolos"
- `[ n $string ]`: comprimento da string é diferente de 0;
- `[ z $string ]`: comprimento da string é igual a 0;
- `[ $string1 = $string2 ]`: string1 é igual a string2;
- `[ $string1 != $string2 ]`: string1 é diferente da string2;
- `[ $int1 -eq $int2 ]`: int1 é igual int2 (válido para números) - "-eq" seria uma abreviação de "equals";
- `[ $int1 -ne $int2 ]`: int1 não é igual int2 (válido para números) - "-ne" seria uma abreviação de "not equals";
- `[ $int1 -gt $int2 ]`: int1 é maior que int2 (válido para números) - "-gt" seria uma abreviação de "greater than";
- `[ $int1 -ge $int2 ]`: int1 é maior ou igual int2 (válido para números) - "-ge" seria uma abreviação de "greater or equal";
- `[ $int1 -lt $int2 ]`: int1 é menor que int2 (válido para números) - "-lt" seria uma abreviação de "lower than";
- `[ $int1 -le $int2 ]`: int1 é menor ou igual int2 (válido para números) - "-le" seria uma abreviação de "lower or equal";
- `[ e $nomearquivo ]`: verifica se um arquivo existe;
- `[ d $diretorio ]`: verifica se valor informado é um diretório;
- `[ f $arquivo ]`: verifica se o arquivo é um arquivo regular (texto, imagem, programa);

## Tomada de decisão com case

Ainda comentando sobre tomada de decisão, podemos utilizar o "case", que aborda de uma maneira um pouco diferente o funcionamento de condições.

```sh
#/bin/bash

echo "Digite 1, 2 ou 3: "
read opc

case $opc in
	"1")
		echo "Você digitou 1! O primeiro número ímpar natural!"
	;;
	"2")
		echo "Você digitou 2! O único número primo que é par!"
	;;
	"3")
		echo "Você digitou 3! O primeiro número primo ímpar!"
	;;
	*)
		echo "O número digitado não está respeitando a condição!"
	;;
esac
```

O exemplo acima demonstra como pode ser feito o uso do "case" em shell script, na qual o "break" seria os dois sinais de ponto e vírgula (";;"), e o asterisco ("`*`") seria o "default"!

## For

O comando "for" é utilizado para realizar um loop determinando uma variável que funcionará como contadora e uma condição a ser satisfeita, sendo um exemplo de laço convencional.

A estrutura do "for" em shell script lembra de diversas outras linguagens, por isso, acredito que se você já tenha tido contato com outras linguagens, você vai compreender facilmente!

```sh
for var1 in val1, val2 … valN; do
        código aqui
done
```

Um exemplo prático imprimindo os números de 1 até 10 seria:

```sh
#!/bin/bash

for i in {1..10}; do
    echo $i
done
```

Perceba que não utilizamos parênteses, apenas um "in" e depois definimos a faixa para que o laço funcione (parecido com linguagens como Python, por exemplo).

## While

Outro tipo de laço muito popular é o "while", que executa tudo que existe em seu conteúdo enquanto uma condição é satisfeita. A estrutura do "while" em shell script é bem simples, veja:

```sh
while [ condição ]; do
        código
done
```

Um exemplo prático para imprimir os números de 1 até 10 seria:

```sh
#!/bin/bash

i=1

while [ $i -lt 11 ]; do
    echo $i

    ((i=$i+1))
done
```
> A parte em que temos `((i=$i+1))` demonstra como seria o incremento de valor 1 na variável i, o mesmo que fazer "i++" em outras linguagens!

Perceba que no caso do "while" como utilizamos colchetes, os espaços entre o início e o fim dos colchetes ainda existe, assim como no "if"!

## Funções

O uso de funções em shell script possibilita que trechos de nosso código sejam reutilizáveis, tornando um código mais organizado e limpo! O uso de funções em shell script é bem interessante, mas, a passagem de parâmetros é algo para se atentar, veja o exemplo abaixo que realiza a soma de dois valores:

```sh
#!/bin/bash

soma(){
    result=$(($1+$2))

    echo "O resultado da soma é: $result!"
}

echo "Informe o valor do número 1: "
read n1
echo "Informe o valor do número 2: "
read n2

soma $n1 $n2
```

Perceba que nos parênteses da função não foi declarado nenhum nome para variáveis, o motivo é: os parâmetros chegam da mesma maneira como chegariam se fossem comandos! Cada parâmetro adicionado em um comando chega com o sinal de cifrão ("$1") seguido da ordem do parâmetro!

Basicamente: o parâmetro chega na função com a variável sendo o número da posição daquele parâmetro, começando do 1!

Caso queira estudar um pouco mais sobre o funcionamento do shell script e se aprofundar sobre como utilizar ele de maneira única, acesse o site do [DevMedia](https://www.devmedia.com.br/introducao-ao-shell-script-no-linux/25778)!

---

Ótimo! Agora que você já compreendeu sobre o funcionamento do shell script e como podemos utilizar suas funcionalidades no nosso cotidiano, o que acha de partirmos para um novo tópico? O tópico de administração de um sistema operacional Linux!

<p align="right">
  <a href="https://github.com/lanjoni/lpi4noobs/blob/main/content/administracao">Próximo -> Administração</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/lpi4noobs#roadmap">Voltar para o menu principal</a>
</p>
