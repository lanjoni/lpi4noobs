# Variáveis de Ambiente

Um dos tópicos mais interessantes quando estamos estudando o funcionamento de um sistema Linux é quando falamos de variáveis de ambiente, que, nada mais são que variáveis definidas para a sessão que está sendo executada para o interpretador de shell, sendo usada para processos específicos gerados a partir do shell.

Para imprimir qualquer variável de ambiente definida é simples: basta utilizar o comando `printenv`.

Um exemplo simples seria para verificar qual interpretador de shell estamos utilizando (em nosso usuário) com o comando:
```sh
$ printenv SHELL
```

## Comando `env`

O comando `env` é responsável por modificar alguma variável de ambiente, veja um exemplo prático:

```sh
env VAR="valor" comando_para_executar opcoes_de_comando
```

## Variáveis de Shell

As variáveis de shell são exclusivas do interpretador de shell para qual ela foi configurada, isso significa que caso você tenha uma variável configurada no bash, por exemplo, mas não tenha ela configurada no zsh, então ela não funcionará em ambos os interpretadores.

## Criando uma variável de Shell

Ainda vamos visualizar com mais detalhes sobre o funcionamento de nosso interpretador de shell, mas, para criarmos uma nova variável de shell é bem simples: basta colocar o nome de nossa variável (em maiúsculo) igual a algum valor. Veja o exemplo abaixo:

```sh
$ VAR='Olá mundo!'
```

E para visualizar seu conteúdo, é simples:

```sh
$ echo $VAR
```

Perceba que para utilizarmos alguma variável de shell necessariamente precisamos de um cifrão ($), demonstrando ser uma variável de shell. A necessidade da criação de uma variável de shell é: só podemos criar novas variáveis de ambiente a partir de uma variável de shell previamente criada.

## Criando uma variável de ambiente

Agora vamos criar uma variável de ambiente: exporando nossa variável de shell criada anteriormente, veja o exemplo abaixo com o comando `export`:

```sh
$ export VAR
```

Agora com o comando `printenv` vamos visualizar nossa variável criada! 
> Um detalhe importante é: toda alteração em nosso interpretador de shell necessita de uma reinicialização de sessão, isto é, reiniciando o terminal ou reiniciando nosso interpretador de shell com o comando `source ˜/.nomedoseuarquivodeconfiguracao` (no caso do bash será "bashrc")

## Praticidade

As variáveis de ambiente e de shell são muito úteis em suas sessões, afinal, é uma maneira completa para definir configurações específicas e tratar valores de uma forma única em seu interpretador de shell. Algumas aplicações necessitam da criação de uma variável de shell para funcionar da maneira correta (como os famosos "version managers"), então, acredito que abrindo o arquivo de configuração de seu interpretador de shell você vai encontrar algumas dessas variáveis.

Caso queira mais detalhes para se aprofundar neste assunto: recomendo a <a href="https://www.digitalocean.com/community/tutorials/how-to-read-and-set-environmental-and-shell-variables-on-linux-pt">publicação no DigitalOcean do Justin Ellingwood</a>!

---

Agora que já implementamos e entendemos o funcionamento de variáveis de ambiente e de shell, o que acha de entendermos como é feito o permissionamnento de arquivos e o que ele pode nos mostrar?

<p align="right">
  <a href="https://github.com/lanjoni/lpi4noobs/blob/main/content/conceitos/permissionamento.md">Próximo -> Permissionamento</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/lpi4noobs#roadmap">Voltar para o menu principal</a>
</p>
