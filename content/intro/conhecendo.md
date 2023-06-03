# Conhecendo distribuições

Uma das coisas mais interessantes sobre o mundo Linux é entender o funcionamento de distribuições. 

Uma distribuição Linux é um sistema operacional completo, contendo o Kernel Linux, pacotes específicos do projeto GNU, além de um gerenciador de pacotes. As distribuições podem ser independentes (surgindo sem se basear em outra) ou podem ser baseadas em outras distribuições. Um exemplo de distribuição independente que podemos citar é o Debian, no qual possui o Ubuntu como uma distribuição baseada. Existem diversas distribuições. Esta alta gama de possibilidades de uso faz com que sejam tão amigáveis para cada usuário em específico. Por isso, vamos conhecer algumas delas.

## Slackware <img align="right" width="100" src="../img/slackware.png" alt="Logo distribuição Slackware">

Famoso por ser a distribuição mais antiga e conhecida, sendo ainda mantida em atividade pela comunidade e pelo seu criador Patrick Volkerding, o Slackware é uma distribuição Linux independente, surgindo em 16 de julho de 1993, com gerenciador de pacotes "Slackpkg". Seu nome surgiu de uma sátira enfatizando "slack" como senso de liberdade, na qual poderíamos traduzir como "preguiça". 

Uma curiosidade sobre a distribuição é que em seus anúncios de versões não tivemos uma versão 5.x ou 6.x, da versão 4.0 pulamos para a versão 7.0.

Algumas distribuições famosas que conhecemos hoje e são baseadas no Slackware:
- Slax
- Porteus
- Kate OS

Para instalar pacotes pelo seu gerenciador utilizamos os seguintes comandos: 
```sh
# slackpkg install
```
> Esse sinal de cerquilha (#) significa que o comando executado no terminal está sendo executado por um usuário **root**. Ainda vamos estudar um pouco sobre este funcionamento. Caso esteja logado como usuário comum: utilize a palavra `sudo` antes do início do comando.

## Debian <img align="right" width="100" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/debian/debian-original-wordmark.svg" alt="Logo distribuição Debian">

Lançado em 16 de agosto de 1993 por Ian Murdock, a distribuição Debian tem sido muito amada por muitos até hoje. O projeto Debian cresceu juntamente de seu gerenciador de pacotes "dpkg", ganhando popularidade e tendo sua primeira versão totalmente estável em 1996. Sua logo em formato de redemoinho foi escolhida por meio de um concurso em 1999, na qual Raul Silva foi o vencedor. A publicação de 26 de agosto de 1999 ainda pode ser vista clicando <a href="https://www.debian.org/News/1999/19990826">aqui</a>.

Algumas distribuições famosas que conhecemos hoje e são baseadas no Debian são:
- Ubuntu
- Linux Mint
- MX Linux
- Deepin
- Kali Linux

Para instalar pacotes pelo seu gerenciador geralmente utilizamos os comandos:
```sh
# apt-get install
```
ou
```sh
# apt install
```

## Red Hat e Red Hat Enterprise Linux <img align="right" width="100" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/redhat/redhat-original-wordmark.svg" alt="Logo Red Hat">

Surgindo em 1995, a Red Hat Inc. tem como seu primeiro "geek" Marc Ewing, que deu este nome à empresa devido ao seu uso contínuo de um boné vermelho do time de lacrosse da Cornell de seu avô, na qual as pessoas sempre diziam: "Se precisar de ajuda, procure o cara do chapéu vermelho".

A Red Hat começou a crescer quando Bob Young, um pequeno empresário que dirigia uma empresa de catálogos de suprimentos em informática teve interesse em conhecer um pouco mais sobre Linux e sobre seu crescente uso, resolvendo comprar CDs do Linux Red Hat de Ewing, esgotando com o estoque de CDs por tantas vezes que resolveram juntar forças para administrar a empresa que começava a crescer.

Tendo sua primeira versão em 22 de fevereiro de 2000, o Red Hat Enterprise Linux é uma distribuição Linux voltada para ambientes empresariais de alta demanda, na qual não possui um ciclo de lançamentos fixo.

Sendo uma distribuição independente, seu principal papel é no desenvolvimento de soluções com suporte empresarial, servidores e redes de trabalho, além de acoplar atualmente diversas soluções específicas para uso em Cloud. Atualmente a Red Hat é parte da IBM.

Diversas distribuições foram baseadas no RHEL devido ao seu gerenciador de pacotes e soluções específicas para servidores, das quais podemos citar:
- Fedora (com patrocínio oficial da Red Hat como distribuição upstream)
- CentOS
- Oracle Linux
- Amazon Linux (baseado tanto no RHEL quanto no Fedora)

Para instalar pacotes pelo seu gerenciador podemos utilizar tanto o `yum` quanto o `dnf`:
```sh
# yum install
```
ou
```sh
# dnf install
```
> Tecnicamente falando podemos dizer que o `dnf` surgiu depois do `yum`, sendo considerado sua versão mais "atualizada".

## Arch <img align="right" width="100" src="../img/arch.png" alt="Logo distribuição Arch">

Uma distribuição popular no mundo Linux é o chamado Arch Linux, surgido em março de 2002 e inicialmente desenvolvido pelo canadense Judd Vinet, mas, atualmente mantido por toda a comunidade. Liderando o projeto até outubro de 2007, Vinet transferiu o controle do projeto para Aaron Griffin. Sua principal filosofia é se baseando em cinco pontos: modernidade, pragmatismo, simplicidade, centralidade no usuário e versatilidade.

O Arch Linux se destaca das demais distribuições por ter um funcionamento um tanto quanto diferente: não existem releases fixas com versões assim como nas demais distribuições citadas, existem *rolling releases*, um sistema no qual o usuário tem acesso às últimas atualizações de pacotes estáveis, mas, o usuário faz o controle dos pacotes que quer instalar e atualizar.

É muito comum vermos sistemas operacionais tendo versões explícitas, pedindo ao usuário realizar atualizações. No Arch você não faz atualizações do sistema operacional como um todo, você seleciona quais pacotes quer atualizar e utilizar, sem a necessidade de uma mudança de visual e atualizações grandes que podem gerar problemas nos componentes do sistema.

Algumas distribuições conhecidas baseadas no Arch Linux:
- Manjaro
- Artix
- ArcoLinux
- Chakra
- EndeavourOS

O gerenciador de pacotes oficial do Arch Linux é o "pacman", mas, você consegue instalar pacotes específicos da comunidade utilizando o "AUR" (Arch User Repository). Para instalar algum pacote no Arch utilizamos o seguinte comando:

```sh
# pacman -S 
```
> O "S" seria para realizar a sincronização de pacotes.

## Gentoo <img align="right" width="100" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/gentoo/gentoo-plain-wordmark.svg" alt="Logo distribuição Gentoo">

Lançado em dezembro de 1999, com sua primeira versão estável em março de 2002, o Gentoo Linux é uma metadistribuição independente inicialmente criada por Daniel Robbins, com objetivo de uma distribuição que fosse compilada a partir do código-fonte, sem pacotes pré-compilados e totalmente otimizada para o Hardware, incluindo apenas por padrão apenas o necessário. 

O que caracteriza esta distribuição é a inexistência em parte de pacotes pré-compilados, ou seja, todo pacote a ser utilizado será compilado em sua máquina, assim como sua instalação que "pode" compilar até mesmo o próprio kernel Linux. Claro, esta seria uma instalação que demoraria muito tempo comparada às outras, mas, seria impossível qualquer pacote não funcionar em seu hardware, afinal, eles foram compilados para e pelo seu hardware.

Algumas distribuições baseadas no Gentoo:
- Funtoo
- Pentoo
- Sabayon

Para atualizações é utilizado o "emerge" e para gerenciamento de pacotes utilizamos o "portage". Para instalar algum pacote utilize o comando "emerge":
```sh
# emerge
```

---

Ótimo! Agora que já conhecemos um pouco sobre as distribuições, o que você acha de vermos um pouco sobre as interfaces gráficas?

<p align="right">
  <a href="https://github.com/lanjoni/lpi4noobs/blob/main/content/intro/interfaces.md">Próximo -> Interfaces gráficas</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/lpi4noobs#roadmap">Voltar para o menu principal</a>
</p>
