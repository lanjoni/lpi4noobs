# Structs

## O que é uma struct?

As "structs" formam estruturas de registros para a necessidade de um agrupamento de dados, é definido como um tipo, e pode conter diversas variáveis. Um exemplo simples para imaginar seria uma struct PESSOA, que tem como dados um id (inteiro), nome (string), telefone (string), endereço (string), data de nascimento (date ou string), altura (float), entre outras possibilidades. 

Normalmente o uso de structs pode ser apresentado em cursos utilizando a linguagem C, por isso, é normal encontrar seu uso em diversas linguagens atualmente.

## Como utilizar structs em Crystal?

A sintaxe para criação de uma struct de exemplo em Crystal é parecido com o exemplo abaixo:

```cr
struct Pessoa
  def initialize(nome : String, email : String)
    @nome = nome
    @email = email
    @data_e_hora = Time.utc
  end
end

pessoa = Pessoa.new("Guto", "guto@he4rt.com")
p! pessoa

puts(pessoa.@nome) # Aqui vamos imprimir apenas o nome dentro da variável pessoa do tipo "Pessoa"!
```

O exemplo acima cria uma struct Pessoa, com nome e email como variáveis do tipo string, além de criar uma variável para data e hora de criação que utiliza "Time.utc" para armazenar a data e hora seguindo o fuso horário UTC.

Posteriormente, atribuímos a variável "pessoa" a struct de tipo "Pessoa" com os dados informados por parâmetro, seguindo de uma impressão do conteúdo da variável em si.

## Compatibilidade com entrada JSON

Passar as entradas como parâmetros pode ser útil em diversos casos, mas, imagine a possibilidade de termos uma entrada em JSON? Com a linguagem Crystal isso é possível e você pode verificar abaixo um exemplo:

```cr
require "json" # Importando a biblioteca JSON

struct Pessoa
  include JSON::Serializable

  getter name : String
  getter email : String
end

json_pessoa = %{{"name": "Guto", "email": "guto@he4rt.com"}}
pessoa = Pessoa.from_json(json_pessoa)
p! pessoa
```

Neste trecho de códigos importamos a biblioteca responsável por manusear os dados que utilizaremos em formato JSON. A struct em si precisa "compreender" que sua entrada de dados será em formato JSON, por isso, surge a necessidade de um "include".

A string é passada como parâmetro e conseguimos visualizar o resultado após imprimir como está a estrutura de nossa variável "pessoa" do tipo "Pessoa" que aceita entradas com trechos em JSON. Incrível não? 

## Múltiplas structs

Certo, explicamos que uma struct pode ser vista como um "tipo de variável", podendo ser utilizado em diversas variáveis, contendo diferentes dados dentro de si... Isso significa que podemos utilizar uma struct dentro de outra? No caso um tipo de struct específico que se completa com outro tipo? A resposta é sim! Veja um exemplo abaixo para criação de uma pessoa com uma struct de endereço:

```cr
require "json"

struct Endereco
  getter rua : String
  getter cidade : String
  getter pais : String

  def initialize(@rua, @cidade, @pais)
  end
end

struct Pessoa
  getter nome : String
  getter email : String
  getter endereco : Endereco

  def initialize(@nome, @email, @endereco)
  end
end

endereco = Endereco.new("Rua 1", "São Paulo", "Brasil")

pessoa = Pessoa.new("Guto", "guto@he4rt.com", endereco)
pp! pessoa
```

Basicamente criamos a struct para armazenar o endereço normalmente (contendo rua, cidade e país), seguido de uma struct para armazenar os dados de uma pessoa, mas, no endereço o tipo de variável ao invés de ser String será do tipo "Endereço", por ser a struct que foi criada anteriormente.

Então vamos criar uma variável "endereco" que irá armazenar o endereço de uma pessoa, e adicionaremos como parâmetro para o campo específico que espera uma variável de tipo "Endereco"! Assim, conseguimos armazenar os dados normalmente! Isso é incrível!

#

O uso de structs pode variar de acordo com a necessidade de uso! Entender seu funcionamento básico vai abrir muitas possibilidades em seu cotidiano!

Caso queira estudar um pouco mais sobre structs seguindo a documentação oficial da linguagem Crystal basta clicar <a href="https://crystal-lang.org/reference/1.7/syntax_and_semantics/structs.html">aqui!</a>

---

O que achou de structs e seu funcionamento na linguagem Crystal?

<p align="right">
  <a href="https://github.com/lanjoni/crystal4noobs/blob/main/content/conceitos/classes.md">Próximo -> Classes</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/crystal4noobs#roadmap">Voltar para o menu principal</a>
</p>
