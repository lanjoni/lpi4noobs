# Su e Sudo

Já ouviu alguma vez alguém falando sobre utilizar um comando chamado "sudo" para executar outro comando? Já se perguntou de onde vem este nome e para que este comando serve? Bom, vamos entender o que significa a palavra **sudo** e desmascarar de uma vez por todas quais são suas funcionalidades!

## Sudo

O comando *sudo* surgiu da necessidade de um usuário comum realizar algum tipo de tarefa que requer permissão do superusuário (**S**uper **U**ser **DO**), por isso, sempre que utilizarmos dele precisarmos tomar muito cuidado, pois, qualquer tarefa como superusuário é permitida. **Qualquer**. Tome cuidado para não realizar nada de tão diferente que possa quebrar o seu sistema!

Além do comando sudo existem outras alternativas, como o comando ***<a href="https://man.openbsd.org/doas">doas</a>*** que vem do OpenBSD.

Instalar algum pacote e movimentar arquivos e diretórios dos quais o usuário comum não tem permissão são algumas das possibilidades que temos ao se utilizar o comando sudo para adquirir privilégios, mas, qualquer usuário tem acesso ao sudo desde que saiba a senha do superusuário root? A resposta é: não. Para se poder fazer uso do sudo primeiramente é necessário instalar o pacote responsável por esta administração (o próprio nome **sudo**), mas, geralmente a maioria das distribuições conhecidas já vem com o pacote instalado. A segunda tarefa a se fazer é adicionar os usuários que deseja ao grupo "sudo". Um exemplo para adicionar determinado usuário a um grupo:

```sh
# usermod -a -G sudo username
```
> Isto vale para qualquer grupo a ser adicionado, sendo "sudo" o nome do grupo e "username" o nome de seu usuário.

Mas, você já parou pra pensar que nem sempre 
