# Combinação

O ato de combinar uma sequência de comandos faz com que o uso de um interpretador de shell seja muito mais interessante, afinal, podemos enviar respostas de comandos para outros e assim chegar em um retorno agradável, claro, para aquilo que desejamos. 

Existem algumas formas de realizar estas combinações, por isso, vamos conhecer algumas:

## Pipe "|"

De uma forma básica, imagine a necessidade de recebermos um retorno de um comando e automaticamente enviarmos para outro, realizando séries de combinações que podem ser muito úteis dependendo do tipo de uso. Imaginou? Esta é a utilidade dos pipes.

Certo, mas, como eu posso utilizar ele? Simples, poderíamos combinar dois comandos que já aprendemos: "ls" e "head", veja um exemplo abaixo.

```sh
$ ls -la | head -n 5
```
> Execute em algum local com mais de 5 arquivos.

Perceba que combinamos o resultado do comando "ls" em um grande trecho de texto, na qual com o "head -n 5" limitamos a mostrar apenas as 5 primeiras linhas de retorno.

Esta combinação de comandos fica ainda mais interessante quando tratamos com o comando "grep".

## Grep

O comando grep é muito conhecido e muito utilizado em combinações de comandos por ter a utilidade de realizar buscas de padrões em arquivos, podendo-se utilizar expressões regulares para buscas mais específicas.

Alguns parâmetros do comando grep:
- -a, --text: trata arquivos binários como arquivos de texto;
- -c: imprime somente a contagem das linhas com expressão;
- -e: define um padrão a ser procurado;
- -h: mostra
- -i: ignora a diferença entre letras maiúsculas e minúsculas;
- -n: mostra o número de cada linha em um arquivo com expressão;
- -s: não exibe mensagens de erro;
- -v: mostra todas as linhas, exceto as linhas com expressão;

Certo, mas como podemos utilizar o comando grep? Bom, primeiramente crie um arquivo de texto bem grande, pra gente poder brincar um pouco. Caso deseje, simplesmente gere um [Lorem Ipsum](https://www.lipsum.com/).

Primeiro vamos simplesmente procurar por todas as palavras "lorem" de nosso texto com o comando:

```sh
$ grep lorem lorem.txt
```
> "lorem.txt" é o nome do arquivo que eu criei, neste caso, troque pelo nome do arquivo que você criou!

Perceba que vai ser retornado todas as áreas em que foi encontrada a palavra "lorem".

Mas, e se quiséssemos reduzir sem mostrar o texto, mas, apenas contando quantas vezes "lorem" apareceu? Simples:

```sh
$ grep -o lorem lorem.txt | wc -l
```
> O parâmetro "-o" reduz a mensagem para imprimir em lista todas as ocorrências da palavra, na qual combinado com o comando "wc" mostramos o número de vezes que essa ocorrência se repete!

Ainda assim podemos buscar uma letra ou palavra no início, ou no final de uma linha, na qual o acento circunflexo ("^") simboliza o início e o cifrão ("$") simboliza o final de uma linha, olha só:

```sh
$ grep -i "^l" lorem.txt
```
> O parâmetro "-i" indica que não existe diferença entre letras maiúsculas e minúsculas!

Para visualizar quais linhas acabam com a letra "s":

```sh
$ grep -i "s.$" lorem.txt
```
> O ponto adicionado foi para simbolizar um ponto final.

Ainda podemos adicionar expressões regulares com o comando grep, veja o exemplo abaixo para encontrar quais parágrafos tem a segunda letra com uma vogal:

```sh
$ grep "^.[aeiou]" lorem.txt
```

As possibilidades de uso do comando grep são infinitas! Por isso, se você quiser se aprofundar um pouco mais no uso do comando em si, recomendo acessar o [Certificação Linux](https://www.certificacaolinux.com.br/comando-linux-grep/) e o [Guia Linux](https://guialinux.uniriotec.br/grep/) da UNIRIO/CCET!

## Saídas com > e >>

Enviar a saída de um comando para um arquivo de texto é algo que pode te auxiliar muito! Por isso, vamos entender um pouco sobre quais são as diferenças entre ">" e ">>"!

- ">": utilizado para enviar um retorno de um comando, apagando todo o conteúdo de um arquivo e sobrescrevendo!
- ">>": utilizado para enviar um retorno de um comando, mas, mantendo o que já se existia antes no arquivo!

### Exemplos práticos: 

O exemplo abaixo vai simplesmente adicionar o texto "oie" ao final do arquivo!

```sh
$ echo "oie" >> lorem.txt
```

O exemplo abaixo vai substituir todo o conteúdo do arquivo deixando apenas o texto "oie"!

```sh
$ echo "oie" > lorem.txt
```

Caso queira estudar um pouco mais sobre compactação e compressão de arquivos no Linux, acesse o guia do site [Certificação Linux](https://www.certificacaolinux.com.br/compactadores-de-arquivos-no-linux/)!

---

Excelente! Já aprendemos como podemos combinar uma série de comandos e fazer com que estas combinações sejam otimizadas! O que acha de entrarmos um pouco no que seria a estrutura de um script chamado "Shell Script?"

<p align="right">
  <a href="https://github.com/lanjoni/lpi4noobs/blob/main/content/pratica/shellscript.md">Próximo -> Shell Script</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/lpi4noobs#roadmap">Voltar para o menu principal</a>
</p>
