# Terminal

Se você já assistiu algum filme que tem algum tipo de hacker escrevendo linhas estranhas em uma tela preta (que muitas das vezes tem uma letra em tons de verde), saiba que você já deve imaginar como é um terminal.

Diferente do que você viu nos filmes, nós não vamos chegar ao ponto de invadir alguma rede em específico, mas, vamos brincar com tudo que esta incrível ferramenta tem a oferecer.

# O que é terminal?

Um conceito que surgiu logo no começo da era da computação, na qual existe até hoje como uma ferramenta essencial em um sistema operacional, o terminal seria basicamente a interface resultante da interação humano-computador, na qual segue o fluxo de entrada do usuário (input), processamento do computador, e retorna uma mensagem ou resposta esperada (saída).

Essa aparência de "tela preta com letras verdes" não é tão difícil de se encontrar, mas, hoje em dia os desenvolvedores ou pessoas que usam o terminal sempre customizam com o design que mais lhes agradam, fazendo com que seja totalmente interativo de acordo com o usuário.

O terminal pode ser simplesmente a única ferramenta em diversas ocasiões (como em configurações de servidores, por exemplo), mas, não se preocupe, atualmente existem diversas ferramentas que impulsionam o seu funcionamento, assim, conseguimos editar trechos de código, executar simples comandos, dividir a tela e muito mais.

Para entender melhor o motivo da existência do terminal, primeiro precisamos entender o que é "Shell" e como ele é aplicado com o terminal, que na realidade, "só é um emulador"...

# Shell

<img align="right" src="https://res.cloudinary.com/practicaldev/image/fetch/s--xrfP8Ah9--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://i.stack.imgur.com/Znlqz.jpg" alt="Imagem demonstrando o processo de entrada do usuário e envio da instrução para o Kernel">

Shell, traduzido do inglês como "concha", é a camada "interlocutora" entre o usuário e o kernel de um sistema operacional. O kernel é responsável por se comunicar diretamente com o hardware, é ele que conversa com seus periféricos e com suas peças. Por ser o núcleo de um sistema operacional, comunicar com ele é algo extremamente perigoso, afinal, qualquer "ordem" errada poderia resultar em uma catástrofe correto?

Dessa necessidade de traduzir a linguagem humana para comandos ao kernel de forma segura surgiu o shell. Nele o usuário poderá enviar comandos específicos que podem ou não ser compreendidos, daí surgem as verificações para saber se um comando é válido.

Basicamente podemos dizer que o usuário entra com algum comando a ser validado pelo interpretador de shell, que decide enviar o comando para o kernel ou não, verificando quem é o usuário que envia o comando, quais são as suas permissões para determinado comando e se o comando é realmente válido.

Existem diversos interpretadores de shell, dos quais irei apresentar alguns para entendermos melhor o conceito:

## Bash

Atualmente mantido pelo projeto GNU e pela Free Software Foundation, o Bash é encontrado como interpretador de shell padrão em diversas distribuições Linux.

## Zsh

Surgindo nos anos 90, o zsh foi uma alternativa ao Bash que atraiu muitos usuários pela sua aparência e funcionalidades adicionais, na qual foi distribuído inicialmente com uma licença respeitando os padrões da Berkeley e teve uma disparada no número de usuários quando a Apple em 2020 anunciou oficialmente que iria adotar o zsh como seu interpretador de shell padrão para sistemas macOS.

## Fish

Sua primeira release foi em 2005 e o fish shell tem agradado diversos usuários pelo mundo por uma alta gama de funcionalidades já inclusas, como ferramentas para navegação em diretórios. 

Para entender um pouco mais sobre os emuladores de terminal, interpretadores shell e como customizá-los acesse meu <a href="https://dev.to/guto/elevando-o-nivel-do-terminal-customizando-suas-funcionalidades-2amm">guia no DEV</a> no qual explico detalhadamente sobre cada um dos interpretadores e como sua utilização pode aumentar muito a produtividade.

---

Perfeito! Agora que você já entendeu como é o funcionamento do terminal, o que é um interpretador de shell e como pode utilizá-lo, vamos entender e conhecer melhor sobre a estrutura de nosso sistema operacional.

<p align="right">
  <a href="https://github.com/lanjoni/lpi4noobs/blob/main/content/conceitos/estrutura.md">Próximo -> Estrutura</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/lpi4noobs#roadmap">Voltar para o menu principal</a>
</p>
