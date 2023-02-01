# Strings

## Manipulação de strings

Bom, agora que estamos trabalhando com strings, que são basicamente um conjunto de caracteres, podemos começar a manipulálos com Crystal! Veja só:
```cr
text = "crystal4noobs"

puts text.size # Utilizado para mostrar o tamanho da string! Neste caso o resultado será 13!

puts text.reverse # Utilizado para mostrar a string reversa! Neste caso o resultado será 'sboon4latsyrc'!
```

Uma peculiaridade interessante sobre o tratamento de strings realizado pela linguagem Crystal é: as strings podem ser vistas como "arrays", na qual cada posição representa uma posição da string! Veja só um exemplo:
```cr
text = "crystal4noobs"

puts text[0] # Irá me retornar o cacactere da primeira posição, neste caso 'c'!
puts text[4] # Irá me retornar o cacarcete da quinta posição, neste caso 't'!
puts text[0, 4] # Mostra os 4 primeiros caracteres!
puts text[0..4] # Mostra os 5 primeiros cacacteres!
```

Para visualizar se uma string contém algum subconjunto de caracteres podemos utilizar a função "includes?"! Olhe este exemplo:
```cr
text = "crystal4noobs"

text.includes?("crystal") # true
```

Para verificar se uma string inicia com determinado conjunto de caracteres basta utilizar a função "starts_with?", e se finaliza com algum conjunto de caracteres a função "ends_with?" olhe:
```cr
text = "crystal4noobs"

puts text.starts_with?("crystal") # true
puts text.starts_with?("lanjoni") # false

puts text.ends_with?("noobs") # true
puts text.ends_with?("follow") # false
```

## Substring

Em algum momento, pode ser que você deseje trabalhar com manipulação de strings, e por isso, vamos observar algumas formas de se realizar esta manipulação.

Caso você deseje alterar alguma parte de uma string:
```cr
text = "Crystal é muito top"

new_text = text.sub("top", "legal") # Aqui estamos alterando a palavra "top" para "legal" e armazenando em uma nova variável, que será impressa abaixo!
puts text
puts new_text

puts text.upcase # Aqui estamos deixando todas as letras desta string maiúsculas!
```

Para verificar se alguma string está vazia ou em branco podemos utilizar:
```cr
vazio = ""
puts vazio.size # 0
puts vazio.empty? # true
puts vazio.blank? # true

espacosembranco = "  \t\n\n\t"
puts espacosembranco.size # 6
puts espacosembranco.empty? # false
puts espacosembranco.blank? # true
```
É muito interessante perceber como no exemplo acima uma varável não é nula por ter espaços em branco inseridos, e sim quando não possui nenhum valor atribuído, e neste caso, espaços em branco são valores que a caracterizam como não sendo nula!

## Conversões de strings

Certo, mas é possível converter strings para valores "int" ou "float" facilmente? A resposta é sim! Observe:
```cr
number = "42.3"

puts number.to_f # Irá retornar 42.3, porém, como "float"!

number = "42"

puts number.to_i # Irá retornar 42, porém, como "integer"!
```

## Quebra de strings

Algo interessante e extremamente útil para se realizar com strings é "quebrá-las", e isto é possível com as funções de "split" que a linguagem Crystal disponibiliza, como por exemplo:
```cr
text = "Esta é uma string!"
puts text
pieces = text.split(" ")
puts pieces # ["Esta", "é", "uma", "string"]

pieces = text.split(/ +/)
puts pieces # ["Esta", "é", "uma", "string"]

text = "nome:segredo"
nome, senha = text.split(":")
puts nome
puts senha
```


## Concatenar strings com variáveis (sprintf e %)

Sim, você pode concatenar um valor de variável em uma nova string para que depois ela possa ser usada, veja alguns exemplos:
```cr
name = "Crystal"
number = 4444

text = "O nome é %s" % name
puts text # O nome é Crystal

text = "O nome é %s e o número é %s" % {name, number} # Tuple
puts text # O nome é Crystal e o número é 4444

text = "O nome é %s e o número é %s" % [name, number] # Array
puts text # O nome é Crystal e o número é 4444

text = "O nome é %{txt} e o número é %{num}" % {txt: name, num: number} # NamedTuple
puts text # O nome é Crystal e o número é 4444

text = sprintf "O nome é %s e o número é %s", name, number
puts text # O nome é Crystal e o número é 4444
```
---

O que achou desse módulo de strings? Agora vamos falar um pouco sobre loops!

<p align="right">
  <a href="https://github.com/lanjoni/crystal4noobs/blob/main/content/conceitos/loops.md">Próximo -> Loops</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/crystal4noobs#roadmap">Voltar para o menu principal</a>
</p>
