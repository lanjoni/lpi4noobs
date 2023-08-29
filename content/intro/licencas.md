# Licenças

## O que são licenças?

Licenças são como contratos de uso, onde o detentos do copyright (em geral o autor) define o que um usuário pode ou não fazer com um produto protegido pelas leis de propriede intelectual. Basicamente podemos dizer que as licenças são responsáveis por definir até onde o usuário pode ir utilizando um determinado software. Sua importância é na determinação dos direitos de propriedade de um software, isto é, definir claramente o que o usuário pode fazer com aquele software.

Entender sobre licenças é essencial para entender Software Livre e Software de Código Aberto (Open-Source).

## Software Livre x Software de Código Aberto

Uma licença que já falamos anteriormente é a licença GNU GPL (que atualmente está em sua versão 3.0), caracterizada por ser uma licença de software livre ou de código aberto (FOSS - Free and Open Source Software - um acrônimo agnóstico para tratar do que for comum às duas vertentes) e garante para o usuário às "quatro liberdades do software" que foram comentadas anteriormente, assim com a "Open Source Definition", derivada indireta das 4 liberdades.

Para manter as liberdades de uso, em produtos derivados, existe o conceito de "copyleft", que é o apelido de uma característica em licenças, como a GNU GPL, que obriga a aplicação da mesma licença em softwares derivados. O Copyleft pode ser diferenciado como "fraco" ou "forte". Copyleft fraco é o que permite o uso do FOSS como parte (em geral lib ou plugin) de um software fechado ou de licença livre, porém incompativel. Esse conceito existe também na coleção de licenças Criative Commons, como "Share Alike".

Licenças FOSS sem Copyleft são cjaadas de "permisivas". Dentre elas temos a MIT e a BSD, que permitem que o software seja diretamante usado por qualquer outro sob qualquer licença. Permite até mesmo o reuso do código sob outra licença, até mesmo fechada.

Software sob licenças FOSS **não** são o mesmo que softwares em "domínio público". As licenças se apoiam na existência do Copyright, mesmo que subvertendo a sua prática padrão e são uma clara normatização do uso, enquanto obras em domínio público são protegidas apenas para manutenção da autoria. (Você não pode dizer que criou a Mona Lisa.)

Uma licenças FOSS exigem que o código-fonte de um software esteja disponível e apesar da confusão comum, não impedem a venda ou cobrança para modificações, manutenção, entre outros serviços que podem ser prestados sob o uso do software em si, ou atrelados à algum determinado produto. Uma licença que proibe isso é a CC-by-nc (Creative Commons - Non Comercial). Essa licença não é considerada FOSS (FSF e OSI concordam), porque restringe a liberdade 0 do software livre e as liberdades 2 e 3 não restringem o "como compartilhar".

A diferença entre FS e OSS está no discurso, vide as falas de [https://www.gnu.org/philosophy/open-source-misses-the-point.html](Stallman) e [https://lists.debian.org/debian-devel/1999/02/msg01641.html](Perens). Suas definições estao relacionadas: A definição de Open Source (em 10 pontos) veio da DFSG (Debian Free Software Gidelines), que é um "detalhamento" das 4 liberdades do SL. Ou seja, todos representam a mesma coisa, com palavras diferentes. As diferenças nas listas de licenças está no "gradiente de cinza" das definições e depende da interpretação, objetivos e interesses dos avaliadores, vide [https://en.wikipedia.org/wiki/Comparison_of_free_and_open-source_software_licences#Approvals](as difernças entre FSF, OSI, Debian e Fedora).

## Algumas licenças
### GNU GPL (GNU General Public License)
- O código-fonte **deve** ser entregue junto ao binário ou facilmente coletado sem oneração para quem adiquiriu o binário.
- Serviços que usam software sob a GPL **não** são obrigados a compartilhar suas modificações.
- Modificações **publicadas** do código **devem** ser lançadas sob a mesma licença.
- Libera o uso de patentes, pertencentes ao autor, envolvidas no código do software.
- Não existe obrigações realcionadas à documentação na licença, mas documentações podem ser igualmente protegidas pela GPL.
- Alguns projetos sob licença GNU GPL: Bash, GIMP, Linux, GNOME, e grande parte do Projeto GNU.

### GNU AGPL (GNU Afero General Public License)
- as mesma garantias da GUN GPL e...
- O código-fonte **deve** ser públicado e acessivel para qualquer usuário de um serviço de rede licenciado sob a AGPL.
- Alguns projetos sob licença GNU AGPL: ScyllaDB, Bacula, Mastodon, e outros.

### Apache
- O código-fonte não precisa ser públicado ou entregue com os binários, apesar de ser um contracenso que inutiliza boa parte da licença.
- Modificações podem ser lançadas sob qualquer licença.
- Mudanças no código **precisam** ser documentadas.
- Proíbe o uso de nomes de marcas registradas encontradas no projeto.
- Alguns projetos sob licença Apache: Android, Apache e Swift.

### BSD (Berkeley Software Distribution)
- O código-fonte não precisa ser públicado ou entregue com os binários, apesar de ser um contracenso que inutiliza boa parte da licença.
- Modificações podem ser lançadas sob qualquer licença.
- Uso de patentes não é explícito.
- Nomes dos autores e colaboradores não podem ser usados para promover produtos derivados do software sem permissão explícita.
- Alguns projetos sob licença BSD: Go, Pure.css e Sentry.

### MIT
- O código-fonte não precisa ser públicado ou entregue com os binários, apesar de ser um contracenso que inutiliza boa parte da licença.
- Modificações podem ser lançadas sob qualquer licença.
- Uso de patentes não é explícito.
- Alguns projetos sob licença MIT: jQuery, Bootstrap e Rails.

### Diagrama para compreendimento do funcionamento das licenças
<img align="center" src="../img/licencas.png" alt="Diagrama para compreendimento de funcionamento das licenças">

> Atenção: Para construir este exemplo utilizei de uma publicação do autor <a href="https://medium.com/code-prestige/como-funcionam-as-licen%C3%A7as-open-source-9ff1da677ccd">Diego Martins de Pinho</a> sobre o funcionamento das licenças.

---

Agora que você já entendeu o funcionamento das licenças e seus tipos de permissionamentos o que acha de colocarmos a mão na massa e prepararmos um ambiente virtual para aprendermos um pouco mais sobre Linux?

<p align="right">
  <a href="https://github.com/lanjoni/lpi4noobs/blob/main/content/intro/instalacao.md">Próximo -> Instalação do Linux</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/lpi4noobs#roadmap">Voltar para o menu principal</a>
</p>
