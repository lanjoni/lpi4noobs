# Arrays

Sabe aquele código em que você precisa armazenar vários valores para uma variável de mesmo nome, mas, não pode necessariamente ser a mesma pois irá sobrescrever aquele valor anterior? Pois é, os "arrays" (também chamados de "vetores") podem te ajudar com isso! 

Um "array" é definido como uma "variável" que pode receber diversos valores de acordo com sua posição indexada! Basicamente, nas estruturas convencionais, sua contagem começa do 0, ou seja, a primeira posição para eles geralmente é 0 (tudo depende da linguagem de programação que você está usando)!

Veja alguns exemplos de "arrays" com Crystal!

```cr
planetas = ["Marte", "Jupipter", "Saturno", "Terra"]
p! planetas           # ["Marte", "Jupipter", "Saturno", "Terra"]
puts typeof(planetas) # Array(String)
puts planetas.size    # 4

integers = [3, 8, -2]
puts typeof(integers) # Array(Int32)

floats = [3.14, 2.1]
puts typeof(floats) # Array(Float64)

misturado = [1, 3.14, "PI"]
puts typeof(misturado) # Array(Float64 | Int32 | String)
```

Epa! Pera lá! Então quer dizer que em cada posição de "array" em Crystal podemos ter uma variável de um tipo diferente? Exatamente! Em Crystal, assim como em diversas outras linguagens, podemos tratar "arrays" com suas tipagens independentes para cada posição, não se limitando exclusivamente ao tipo inicial!

## Índices

Os índices são os números que indicamos para cada posição de array (as nossas "casinhas" do vetor). Vamos dar uma olhada em como cada índice é tratado na linguagem Crystal?

```cr
planetas = ["Mercúrio", "Vênus", "Terra", "Marte", "Júpiter"]
puts planetas[0]  # Mercúrio
puts planetas[1]  # Vênus
puts planetas[-1] # Júpiter

puts planetas[0, 3]  # ["Mercúrio", "Vênus", "Terra"]
puts planetas[0..3]  # ["Mercúrio", "Vênus", "Terra", "Marte"]
puts planetas[0...3] # ["Mercúrio", "Vênus", "Terra"]
```

Perceba: os índices começam a ser contador a partir do 0, como dito anteriormente! Além disso, olhe só quando informamos um índice com valor negativo (neste caso o "-1")... Basicamente ele retorna o último índice, assim como se fosse "-2" retornaria o penúltimo, e assim por diante...

Agora, perceba que temos diferentes formas para imprimir "uma fatia" dos valores de um array. No primeiro exemplo, mostramos os três primeiros itens a partir do índice 0 (sem contar ele), porém, podemos pensar como se fossem os três primeiros, começando do índice 0 (contando ele), mas, sem contar o último índice. Depois, aida temos o caso que utiliza "..", delimitando qual o primeiro índice e qual o último índice a ser mostrado, assim, definindo o intervalo de índices a serem apresentados. Por último, temos um exemplo com "..." que possui funcionamento similar ao penúltimo exemplo.

## "Each with index"

"Each with index" é o nome de uma função na qual conseguimos imprimir um indíce e valor de array juntos! Veja um exemplo:

```cr
planetas = ["Mercúrio", "Vênus", "Terra", "Marte", "Júpiter"]

# enumerando...
planetas.each_with_index { |planeta, idx|
  puts "#{idx}: #{planeta}"
}
```

No exemplo acima iremos imprimir um valor de índice de array seguido de seu valor (conteúdo)! Esta é uma forma muito útil para realizar tratamentos específicos com índices!

## Adicionando valores

Certo, mas e se algum dia eu quiser adicionar um valor para um array em sua última posição? Por exemplo: imagine que eu tenho uma sequência de planetas e num belo dia desejo adicionar mais um valor, independente da casa, surgindo de preferência no último índice... Como faríamos isso? Simples! Temos duas maneiras de realizar tal tarefa, veja:

```cr
planetas = ["Marte", "Júpiter", "Saturno"]

# append / push / <<
planetas << "Plutão"
puts planetas # ["Marte", "Júpiter", "Saturno", "Plutão"]

planetas.push("Vênus")
puts planetas # ["Marte", "Júpiter", "Saturno", "Plutão", "Vênus"]
```

Com o "append" ("<<") que possui sintaxe muito parecida com linguagens como "C++" para se adicionar algum elemento, podemos utilizar este símbolo no nome de variável de nosso array. Podemos ainda utilizar a função "push", que será responsável por adicionar os valores que vierem em sua passagem de parâmetros!

## Criando arrays sem tamanhos pré-definidos

Definir um tamanho de array pode não ser uma tarefa fácil, afinal, não é sempre que sabemos a quantidade de índices que podemos ter, não é mesmo? Bom, veja agora como podemos criar arrays sem a necessidade de tamanhos definidos anteriormente:

```cr
# vazio = []       # ERRO! Não podemos simplesmente definir um array sem seu tipo!

vazio = [] of Int32 # Aqui criamos um array em formato para números inteiros
puts vazio.size   # 0 - Função responsável por trazer o tamanho de um array (quantidade de índices)
puts vazio.empty? # true - Função para verificar se um array está vazio!

vazio << 23
puts vazio.size   # 1
puts vazio.empty? # false

# vazio << 3.14  # ERRO! Não podemos inserir valores para números não inteiros em um array declarado como recebendo apenas números inteiros

outro = Array(Int32).new
puts typeof(outro) # Array(Int32) - Função para retornar tipo da variável, sendo neste caso um array de números inteiros!
puts outro.size    # 0
```

## Contando quantidade de vezes que um número aparece

Já parou pra pensar como deve ser difícil contar a quantidade de vezes que um número aparece em uma string? Veja como é fácil com Crystal!

```cr
texto = "123456789112777"
count = [0] * 10

texto.each_char { |chr|
  count[chr.to_i] += 1
}

count.each_with_index { |value, idx|
  puts "#{idx} #{value}"
}
```

Certo, mas, qual a relação disso com arrays? Simples: a string é convertida para um array, na qual cada número recebe um índice, e daí são feitas estas comparações!

## Operações com arrays

Já pensou poder somar arrays? Pois é, isso é possível, sendo bem mais fácil do que você imagina, veja:

```cr
x = [2, 3, 4]
y = [5, 6, 7]
p! x
p! y
z = x + y
p! z
```

E multiplicar? Podemos imprimir um array mais de uma vez? Claro!

```cr
x = [1, 2] * 3
y = [0] * 10
p! x
p! y
```

## Seleção (filter e grep)

Já parou pra pensar como seria incrível a possibilidade de se filtar o conteúdo de um array? Pois é, isto é muito simples com Crystal! Veja:

```cr
numeros = [10, 20, 7, 21, 5]
puts numeros # [10, 20, 7, 21, 5] - Retorno de todos os itens, o array completo!
small = numeros.select do |num|
  num > 10
end
puts small # [20, 21] - Retorno dos valores maiores que o número 10! 
puts numeros.select { |num| num > 10 } # [20, 21] - Retorno dos valores na qual seus módulos sejam maiores que 10!
puts numeros # [10, 20, 7, 21, 5] - Retorno de todos os itens, o array completo!
puts ""

big = numeros.select! do |num|
  num < 10
end
puts big # [7, 5] - Retorna tods os números que são menores que 10!
```

## Sample e Shuffle

Para poder imprimir um valor aleatório de um array (apenas por curiosidade) você pode utilizar "sample"! Veja:

```cr
planetas = ["Mercúrio", "Vênus", "Terra", "Marte", "Júpiter"]
puts planetas
puts planetas.sample
```

Caso você queira mostrar as posições do array, porém, apresentando cada uma de forma aleatória você pode seguir o exemplo abaixo:

```cr
planetas = ["Mercúrio", "Vênus", "Terra", "Marte", "Júpiter"]
puts planetas
puts planetas.shuffle
```

## Join

Imagine que você tenha um array, mas queira transformar em uma string (para utilizar em algum JSON ou algo do tipo), saiba que isto é completamente possível utilizando "join", na qual você pode observar no exemplo a seguir:

```cr
nomes = ["Crystal", "4", "Noobs"]
puts nomes.join "-" # Crystal-4-Noobs
```

## Manipular valores de um array

Agora iremos verificar algumas maneiras para manipular os valores de um array!

- Delete (apagar valores) pelo valor
```cr
planetas = ["Mercúrio", "Vênus", "Terra", "Marte", "Júpiter"]
puts planetas
planetas.delete("Terra")
puts planetas # ["Mercúrio", "Vênus", "Marte", "Júpiter"]
```

- Delete (apagar valores) pelo índice
```cr
planetas = ["Mercúrio", "Vênus", "Terra", "Marte", "Júpiter"]
planetas.delete_at(1)
puts planetas # ["Mercúrio", "Terra", "Marte", "Júpiter"]
```

- Includes (inclui algum valor?)
```cr
planetas = ["Mercúrio", "Vênus", "Terra", "Marte", "Júpiter"]
puts planetas.includes?("Vênus") # true
```

- Insert (inserir em determinada posição)
```cr
planetas = ["Mercúrio", "Vênus", "Terra", "Marte", "Júpiter"]
planetas.insert(1, "Saturno")
puts planetas # ["Mercúrio", "Saturno", "Vênus", "Terra", "Marte", "Júpiter"]
```

- Uniq (apagar valores repetidos)
```cr
planetas = ["Mercúrio", "Vênus", "Mercúrio", "Terra", "Marte", "Júpiter", "Mercúrio"]
planetas.uniq!
puts planetas # ["Mercúrio", "Vênus", "Terra", "Marte", "Júpiter"]
````

- First (exibir primeiro valor de um array)
```cr
planetas = ["Mercúrio", "Vênus", "Mercúrio", "Terra", "Marte", "Júpiter", "Mercúrio"]
puts planetas.first # Mercúrio
puts planetas[0]    # Mercúrio
```

---

Eaí, gostou de trabalhar com arrays? Pronto para o próximo capítulo?

<p align="right">
  <a href="https://github.com/lanjoni/crystal4noobs/blob/main/content/conceitos/hash.md">Próximo -> Hash</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/crystal4noobs#roadmap">Voltar para o menu principal</a>
</p>
