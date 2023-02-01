# Funções

## Sintaxe

As funções existem na programação para executar uma determinada tarefa que pode se repetir de diversas formas, automatizando um processo que muitas das vezes pode se tornar repetitivo. No exemplo abaixo iremos obsevar como é construída uma função simples utilizando a linguagem Crystal:

```cr
def soma(a : Int32, b : Int32)
    return a + b
end

puts(soma(1, 2))
```

O exemplo acima irá exibir na tela o resultado de uma soma, recebendo dois números como parâmetros! Perceba que nos parâmetros temos a sintaxe "[nome da variável] : [tipo da variável]", sendo necessário existir ambos os espaços para essa função, tendo um retorno com a soma de ambos os números e finalizando a função com "end".

Enquanto algumas linguagens possuem funções com nome como "function" ou "fn", a linguagem Crystal utiliza o nome "def" assim como outras linguagens como Python e Ruby!

## Tipos de parâmetros

Certo, então, "Int32" é utilizado como o tipo de parâmetro para números inteiros? Sempre eu preciso informar quais parâmetros eu espero em uma função? A resposta é simples e clara: não! 

Você pode simplesmente informar que vai receber duas variáveis, independente do tipo, e somá-las, por exemplo... Veja no exemplo abaixo: 

```cr
def soma(a, b)
    return a + b
end

puts(soma(1, 2))
```

Neste exemplo acima não informamos o tipo da variável que deveríamos receber e ainda assim o código é funcional! 

Então quer dizer que quando quisermos forçar um tipo de variável como parâmetro basta que adicionemos ": [tipo da variável]"? Isso mesmo! Simples não?

## Tipos de retornos

Assim como definimos o tipo de parâmetro conseguimos definir o tipo de retorno de uma função? Claro! É tão simples que possui até a mesma sintaxe que para forçar um tipo de parâmetro:

```cr
def soma(a, b) : String
    return "O resultado é #{a + b}"
end

puts(soma(1, 3))
```

Perceba que basicamente seguimos a mesma regra para definir um tipo para qualquer variável!

## Splat, uma maneira ágil de tratar múltiplos parâmetros

Vamos supor que queremos criar uma função que some números, mas neste caso não apenas dois ou três e sim uma quantidade não definida, podendo variar de diversas maneiras... Isto é possível? A resposta é sim! Veja um exemplo abaixo:

```cr
def soma(*n : Int32)
    n.sum
end

puts(soma(1, 3))
```

Basicamente como parâmetro devemos adicionar um "*" (utilizado para indicar ponteiros em outras linguagens como C), o tipo de parâmetro a ser recebido e dentro da função basta utilizar ".sum" para somar os elementos que compõem a "tupla" formada!

Caso queira estudar um pouco mais sobre funções seguindo a documentação oficial da linguagem Crystal basta clicar <a href="https://crystal-lang.org/reference/1.6/syntax_and_semantics/new%2C_initialize_and_allocate.html">aqui!</a>

---

Eaí, o que achou das funções na linguagem Crystal? Vamos para o próximo tópico?

<p align="right">
  <a href="https://github.com/lanjoni/crystal4noobs/blob/main/content/conceitos/structs.md">Próximo -> Structs</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/crystal4noobs#roadmap">Voltar para o menu principal</a>
</p>
