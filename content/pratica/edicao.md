# Edição de arquivos

A edição de arquivos pode ser feita de diversas maneiras utilizando um sistema Linux, por isso, vamos destacar algumas, mas, em sua maioria editores que funcionam dentro do próprio terminal, sendo que para aqueles que gostam de se aventurar na tecnologia e costumam programar, saiba que existem editores específicos para estas tarefas, na qual configurados corretamente podem aumentar **muito** a sua produtividade. Bora conhecer alguns?

## Gedit

Um editor de texto compatível com interface gráfica do projeto GNOME, o "gedit" possui funcionalidades semelhantes ao que temos no windows como um "bloco de notas", sendo possível de ser acessado via interface gráfica, podendo ser instalado ou não, mas, suportando diversas funcionalidades e até mesmo suportando "text highlighting" em algumas linguagens de programação por padrão. Para utilizar basta executar o comando `gedit nome_do_seu_arquivo`!

Sua primeira versão surgiu em 12 de fevereiro de 1999!

<img src="../img/gedit.png" alt="Editor de texto GEDIT">

## GNU Nano

Surgindo em 1999, mas fazendo parte do projeto GNU a partir de 2001, o GNU Nano é um editor de texto que, atualmente, está presente por padrão na maioria das distribuições Linux, utilizado totalmente via terminal, sendo leve e prático para permitir que o usuário possa realizar simples modificações em textos ou até mesmo editar códigos. Para utilizar basta executar o comando `nano nome_do_seu_arquivo`!

Sua sintaxe é bem simples e intuitiva, afinal, existe um menu na barra inferior demonstrando as funcionalidades, dentre elas o famoso "salvar e sair" pode ser feito apertando `CTRL + O` para salvar e `CTRL + X` para sair!

<img src="../img/nano.webp" alt="Editor de texto GNU Nano">

## VI

Tendo seu primeiro release em 1976, o "vi" ficou muito famoso na época por ser um editor prático, simples, leve, intuitivo e que possuia um suporte para funcionalidades específicas diretamente no terminal, possibilitando sua popularização! Podendo ser utilizado para edições simples e edições específicas, o vi pode estar ou não presente por padrão em sua distribuição, sendo necessário utilizar o comando `vi nome_do_seu_arquivo` para começar a utilizar!

O famoso "salvar e sair" que muitos brincam sobre "necessitar de forçar o desligamento do PC para sair do VI" pode ser feito de forma simples:
- Tecle a letra `i` para entrar no modo de inserção de texto;
- Após acabar de inserir textos, aperte `esc` para voltar para o modo de comandos;
- Agora digite `:wq`, na qual os dois pontos ":" indicam um comando a ser digitado, "w" para salvar (escrever - write - traduzido) e "q" para sair (quit - traduzido);

Simples não é?

<img src="../img/vi.webp" alt="Editor de texto VI">
