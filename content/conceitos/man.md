# Man

O comando ***man*** é utilizado para apresentar um manual que aborda as principais funcionalidades de um determinado comando, sendo útil para todos os momentos em que você estiver na dúvida sobre como comando pode ser usado, quais parâmetros pode receber e quais finalidades possui.

Para ser utilizado é bem simples, basta seguir a estrutura:

```sh
$ man [opções] comando
```

O nome "opções" são todos os parâmetros que o usuário pode adicionar para alterar a visualização do manual do comando pedido. Os principais parâmetros disponíveis são:

- **-a**: apresenta ***todas*** as páginas seguindo a ordem definida em "/etc/manpath.config";
- **-f** ou **-whatis**: apresenta uma pequena descrição sobre o comando;
- **-k palavra** ou **-apropos palavra**: apresenta um resultado baseado em uma busca nos índices do manual de acordo com a palavra fornecida;

