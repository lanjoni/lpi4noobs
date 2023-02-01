# Hash

Hashs são geralmente utilizados para comparações de dados extensos ou secretos, permitindo o mapeamento de valores dentro de uma variável! Veja alguns exemplos:

```cr
planetas = {
  "Marte"    => 1,
  "Júpiter" => 2,
  "Saturno"  => 3,
  "Terra"   => 4,
}
```

No exemplo acima realizamos a atribuição de valores, na qual são definidos seus valores seguido de suas devidas posições (esquema de índices similar aos arrays).

```cr
puts planetas # Imprime os valores com a mesma sintaxe utilizada para atribuir os valores!
puts planetas.size # Imprime o tamanho, sendo neste caso a quantidade de itens!
puts planetas.keys # Imprime os valores como se fosse um array!
```

Ainda assim podemos atribuir valores de forma separada à atribuição, ou seja, um valor único:

```cr
planetas["Plutão"] = 7 # Aqui atribuímos o valor para a posição 7 (valor 7)

puts planetas.has_key?("Plutão") # true
puts planetas.has_key?("Lua")  # false

puts planetas.has_value?(3) # true
puts planetas.has_value?(8) # false
```

## Verificação de valores

As verificações de valores possuem funções específicas, assim como no exemplo acima, mas podemos ainda definir os valores e quantidades de cada valor a serem verificados... Veja o exemplo:

```cr
palavras = ["gato", "cachorro", "cobra", "gato", "joaninha", "formiga", "gato", "cachorro"]
count = {} of String => Int32 # Hash vazio!

palavras.each { |palavra|
  if !count.has_key?(palavra)
    count[palavra] = 0
  end
  count[palavra] += 1
}

count.each { |palavra, cnt|
  puts "#{palavra} #{cnt}"
}
```

No exemplo acima realizamos a verifação de cada item, sendo realizada uma contagem de acordo com o índice informado, sendo assim, a cada vez que tínhamos um item com valor igual ao do índice, seu valor aumentava 1 (para que assim pudéssemos verificar a quantidade de itens iguais temos)!

## Merge

A função "merge" é utilizada para adicionar valores em um hash! Podemos adicionar apenas no momento de impressão (utilizando a função "merge") ou adicionar um valor permanente (utilizando a função "merge!"), veja:

```cr
planetas = {
  "Marte"    => 1,
  "Júpiter" => 2,
  "Saturno"  => 3,
  "Terra"   => 4,
}
puts planetas # {"Marte" => 1, "Júpiter" => 2, "Saturno" => 3, "Terra" => 4} # Valor original
puts planetas.merge({"Vênus" => 5, "Marte" => 10}) # {"Marte" => 10, "Júpiter" => 2, "Saturno" => 3, "Terra" => 4, "Vênus" => 5} # Valores alterados, porém não é definitivo: o valor permanece apenas para impressão!
puts planetas # {"Marte" => 1, "Júpiter" => 2, "Saturno" => 3, "Terra" => 4}

puts planetas.merge!({"Plutão" => 5, "Marte" => 20}) # {"Marte" => 20, "Júpiter" => 2, "Saturno" => 3, "Terra" => 4, "Plutão" => 5} # O valor alterado permanece! O sinal de exclamação força a alteração do hash!
puts planetas # {"Marte" => 20, "Júpiter" => 2, "Saturno" => 3, "Terra" => 4, "Plutão" => 5}
```

## Manipulação

Para apagar algum valor de um hash é simples! Podemos simplesmente informar seu valor, veja:

```cr
planetas = {
  "Marte"    => 1,
  "Júpiter" => 2,
  "Saturno"  => 3,
  "Terra"   => 4,
}

puts planetas.delete("Marte") # 1 # Índice do valor que foi excluído!
puts planetas # {"Júpiter" => 2, "Saturno" => 3, "Terra" => 4}
```

Além da função "delete" podemos utilizar a função "reject" para apagar um elemento ou apenas não retorná-lo no momento de impressão, veja:

```cr
planetas = {
  "Marte"    => 1,
  "Júpiter" => 2,
  "Saturno"  => 3,
  "Terra"   => 4,
}

puts planetas.reject("Marte") # {"Júpiter" => 2, "Saturno" => 3, "Terra" => 4}
puts planetas # {"Marte" => 1, "Júpiter" => 2, "Saturno" => 3, "Terra" => 4} # O valor continua lá, apenas não foi impresso no exemplo anterior

puts planetas.reject!("Marte") # {"Júpiter" => 2, "Saturno" => 3, "Terra" => 4} # Adicionando o sinal de exclamação é feita a remoção do valor!
puts planetas # {"Júpiter" => 2, "Saturno" => 3, "Terra" => 4}
```

Certo, mas e se for necessário limpar um hash? Simples, podemos utilizar a função "clear"! Observe:

```cr
planetas = {
  "Marte"    => 1,
  "Júpiter" => 2,
  "Saturno"  => 3,
  "Terra"   => 4,
}

puts planetas.clear # {}
puts planetas       # {}
```

Para filtrar um hash podemos utilizar a função "select"! Veja:

```cr
planetas = {
  "Marte"    => 1,
  "Júpiter" => 2,
  "Saturno"  => 3,
  "Terra"   => 4,
}

puts planetas.select { |name, number| number > 2 && name.includes?("r") } # {"Saturno" => 3, "Terra" => 4}
puts planetas # {"Marte" => 1, "Júpiter" => 2, "Saturno" => 3, "Terra" => 4}

puts planetas.select! { |name, number| number > 2 && name.includes?("r") } # {"Saturno" => 3, "Terra" => 4}
puts planetas # {"Saturno" => 3, "Terra" => 4}
```

No exemplo acima perceba que é feita uma verificação do valor (neste caso "name") e índice (neste caso "number"), sendo neste caso quando "name" incluir uma letra "r" em seu nome e seu "number" for maior que 2. Perceba que ao utilizar o sinal de exclamação é forçada uma alteração!

## Hash multi-dimensional

A possibilidade de se criar um hash multi-dimensional abre um leque de diversas possibilidades utilizando eles! Veja um exemplo de uso e filtragem:

```cr
planetas = {
  "Marte" => {
    "cor" => "Vermelho e marrom...",
  },
  "Júpiter" => {
    "cor" => "Marrom e laranja...",
  },
  "Saturno" => {
    "cor" => "Dourado, marrom e com tons de verde...",
  },
  "Terra" => {
    "cor" => "Azul, marrom, verde e com tons de branco...",
  },
}

puts planetas["Marte"]["cor"] # Vermelho e marrom...
```

Sua sintaxe é "similar" a um arquivo JSON, trocando o sinal de dois pontos ":" para uma flecha "=>"!

---

Eaí, gostou de estudar um pouco mais sobre hashs? Achou útil? Vamos agora introduzir conceitos por trás de manipulações de arquivos...

<p align="right">
  <a href="https://github.com/lanjoni/crystal4noobs/blob/main/content/conceitos/arquivos.md">Próximo -> Arquivos</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/crystal4noobs#roadmap">Voltar para o menu principal</a>
</p>
