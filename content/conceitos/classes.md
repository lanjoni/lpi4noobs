# Classes

## O que são classes?

Parecidas com as "structs", as classes tem como objetivo criar um novo tipo de dado para seu projeto, utilizando de conceitos voltados para a orientação à objeto, podendo utilizar métodos além de variáveis.

Poderíamos dizer que uma classe é "quase" a mesma coisa que uma struct, pois surgiu de um conceito muito parecido, mas, a possibilidade de se adicionar muito mais do que apenas simples variáveis fez com que as classes e a orientação a objetos fossem grandes amigas!

## Como podemos utilizar as classes na linguagem Crystal?

Veja um exemplo abaixo em que criamos uma classe "Pessoa" que recebe o nome e altura:

```cr
class Pessoa
    def initialize(nome : String, altura : Float64)
        @nome = nome
        @altura = altura
    end

# Getters (Buscando o valor dessas variáveis)

    def nome
        @nome
    end

    def altura
        @altura
    end

# Setters (Atribuindo valor para estas variáveis)

    def nome(value)
        @nome = value
    end

    def altura(value)
        @altura = value
    end
end
  
pessoa = Pessoa.new(nome: "Guto", altura: 1.7)
puts pessoa.nome # Guto
puts pessoa.altura # 1.70

pessoa.nome("João") # Atualizando o valor do nome da variável "pessoa" do tipo "pessoa"

puts pessoa.nome # João
```

No exemplo acima criamos uma variável "pessoa" do tipo "Pessoa", recebendo um valor para nome e um valor para altura. Veja que preparamos os métodos "Getters" e "Setters", responsáveis por "buscar" e "atribuir" valores às variáveis da classe respectivamente.

Logo após criar a nossa variável perceba que atualizamos o seu valor, passando agora o nome para "João". A sintaxe para atualização de um valor não é utilizando o símbolo "=", mas, passando o valor a ser atualizado por parâmetro utilizando os parênteses!

## JSON

Se com as structs eu consegui criar uma variável utilizando apenas os dados de entrada em formato JSON, então, eu consigo fazer isso utilizando classes? A resposta é: sim. Veja o exemplo abaixo:

```cr
require "json"

class Pessoa
    include JSON::Serializable

    property nome : String
    property altura : Float64

    def initialize(@nome, @altura)
    end
end

str = %{{"nome": "Guto", "altura": 1.7}}
  
pessoa = Pessoa.from_json(str)
puts pessoa.nome # Guto
puts pessoa.altura # 1.7

pessoa.nome = "João"

puts pessoa.nome # João
```

No exemplo acima realizamos a importação da biblioteca responsável por controlar os dados em formato JSON, depois criamos nossa classe, na qual você consegue notar algumas diferenças marcantes em seu conteúdo!

Logo depois, criamos uma string que deve conter nossos dados em formato JSON e utilizamos para instanciar nossa nova variável "pessoa" do tipo "Pessoa".

Para atualizar algum valor, perceba que dessa vez utilizamos o símbolo "=" ao invés de passar algum valor como parâmetro!

---

O que achou de trabalhar com classes na linguagem Crystal?

<p align="right">
  <a href="https://github.com/lanjoni/crystal4noobs/blob/main/content/finalizacao/finalizacao.md">Próximo -> Finalização</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/crystal4noobs#roadmap">Voltar para o menu principal</a>
</p>
