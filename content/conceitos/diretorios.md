# Diretórios

## Listagem

Diversas funcionalidades são possíveis quando utilizamos Crystal, dentre elas a listagem de conteúdo é uma das funcionalidades que permitem gerenciar nossos diretórios. Observe o exemplo abaixo:

```cr
if ARGV.size != 1
    puts "Você precisa informar o caminho do diretório!"
    exit 1
end

path = ARGV[0]

dr = Dir.new(path)
dr.children.each { |thing|
    puts thing
}
```

O exemplo acima irá retornar o conteúdo completo de um diretório, sendo necessário informar o caminho para que se possa visualizar seu conteúdo!

## Visualizar caminho

Para visualizar o caminho completo em que você se encontra basta utilizar a seguinte função: 

```cr
puts Dir.current # Similar ao comando pwd!
```

## Biblioteca 'file_utils'

A biblioteca chamada 'file_utils' possui esse nome por conter funções específicas para o gerenciamento de arquivos e diretórios! Ela é extremamente útil em diversos casos! Veja alguns exemplos: 

```cr
require "file_utils" # Aqui realizamos a importação da biblioteca

tempdir = File.tempname # Aqui definimos o nome do diretório a ser criado
FileUtils.mkdir(tempdir) # A função FileUtils.mkdir() cria um diretório - daí vem o nome com o comando 'mkdir'
FileUtils.cd(tempdir) # A função FileUtils.cd() entra em um diretório específico, por isso é utilizado em seu nome o comando 'cd'
FileUtils.rm_rf(tempdir) # A função FIleUtils.rm_rf() remove um arquivo ou diretório de forma forçada, que seria equivalente ao comando 'rm -rf'
```

Esta biblioteca possui ainda diversas outras funcionalidades e comandos que você pode verificar clicando <a href="https://crystal-lang.org/api/1.5.1/FileUtils.html">aqui!</a>

---

Eaí, gostou de ver como é o gerenciamento de diretórios na linguagem Crystal? Vamos para mais uma aventura?

<p align="right">
  <a href="https://github.com/lanjoni/crystal4noobs/blob/main/content/conceitos/funcoes.md">Próximo -> Funções</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/crystal4noobs#roadmap">Voltar para o menu principal</a>
</p>
