# Instalação

Bom, se você chegou até aqui, quer dizer que realmente está interessado em dar continuade nesse aprendizado, e agora, iremos instalar o compilador em Crystal em seu computador pessoal.

## Sistemas Operacionais
- [macOS](https://github.com/lanjoni/crystal4noobs/blob/main/content/intro/instalacao.md#macos)
- [Windows](https://github.com/lanjoni/crystal4noobs/blob/main/content/intro/instalacao.md#windows)
- [Debian/Ubuntu e derivados](https://github.com/lanjoni/crystal4noobs/blob/main/content/intro/instalacao.md#debianubuntu-e-derivados)
- [Red Hat/Fedora e derivados](https://github.com/lanjoni/crystal4noobs/blob/main/content/intro/instalacao.md#red-hatfedora-e-derivados)
- [OpenSUSE](https://github.com/lanjoni/crystal4noobs/blob/main/content/intro/instalacao.md#opensuse)
- [Arch Linux/Manjaro e derivados](https://github.com/lanjoni/crystal4noobs/blob/main/content/intro/instalacao.md#arch-linuxmanjaro-e-derivados)
- [Gentoo](https://github.com/lanjoni/crystal4noobs/blob/main/content/intro/instalacao.md#gentoo)
- [FreeBSD](https://github.com/lanjoni/crystal4noobs/blob/main/content/intro/instalacao.md#freebsd)
- [Snaps](https://github.com/lanjoni/crystal4noobs/blob/main/content/intro/instalacao.md#snaps)

Nota: sempre que for visto "{REPOSITORY}" em algum link para instalação, altere esta palavra para o nome e versão de sua distribuição! Para mais informações clique <a href="https://software.opensuse.org/download.html?project=devel%3Alanguages%3Acrystal&package=crystal">aqui!</a>

Teve algum problema com a instalação? Clique <a href="https://crystal-lang.org/install/">aqui</a> para acessar a documentação oficial de instalação!

---

### macOS
A instalação do Crystal para o macOS é feita utilizando o gerenciador de pacotes <a href="https://brew.sh/">Homebrew</a>. Para realizar sua instalação utilize os seguintes comandos no terminal:
```
brew update
brew install crystal
```
Para instalar uma nova versão do Crystal basta executar:
```
brew upgrade crystal
```
Para mais informações sobre a instalação do Crystal no macOS clique <a href="https://crystal-lang.org/install/on_mac_os/">aqui!</a>

#

### Windows
Caso você esteja utilizando Windows, recomendo que instale alguma distribuição Linux de sua preferência para utilizar juntamente do WSL. O compilador Crystal ainda não consegue rodar nativamente no Windows, e por isso, sua compatibilidade é gerenciada pelo WSL no Windows. Para mais informações sobre a instalação do WSL clique <a href="https://docs.microsoft.com/en-us/windows/wsl/install">aqui!</a>

#

### Debian/Ubuntu e derivados
Para iniciar nossa intalação, primeiramente precisamos adicionar o repositório deb oficial do Crystal, e para isso execute em seu terminal:
```
curl -fsSL https://crystal-lang.org/install.sh | sudo bash
```
ou 
```
curl -fsSL https://crystal-lang.org/install.sh | sudo bash -s -- --channel=nightly
```
Para dar continuidade em nosso setup manual exeute:
```
echo "deb http://download.opensuse.org/repositories/devel:/languages:/crystal/{REPOSITORY}/ /" | sudo tee /etc/apt/sources.list.d/crystal.list

curl -fsSL https://download.opensuse.org/repositories/devel:languages:crystal/{REPOSITORY}/Release.key | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/crystal.gpg > /dev/null
```
Agora que os repositórios já estão proprieamente adicionados, vamos instalar o compilador Crystal:
```
sudo apt update
sudo apt install crystal
```

Na documentação oficial é recomendado a adição de algumas bibliotecas para funcionalidades específicas, e caso queira adicionar, execute:
```
sudo apt install libssl-dev
sudo apt install libxml2-dev
sudo apt install libyaml-dev
sudo apt install libgmp-dev
sudo apt install libz-dev
```

Quando uma nova versão do Crystal for lançada, você pode instalá-la executando:
```
sudo apt update
sudo apt install crystal
```

#

### Red Hat/Fedora e derivados
Para adicionar os pacotes oficiais de instalação do compilador Crystal execute:
```
curl -fsSL https://crystal-lang.org/install.sh | sudo bash
```
ou
```
curl -fsSL https://crystal-lang.org/install.sh | sudo bash -s -- --channel=nightly
```

Agora, com os repositórios devidamente adicionados, execute:
```
sudo yum install crystal
```
ou 
```
sudo dnf install crystal
```

Para instalar futuras atualizações, basta executar:
```
sudo yum update crystal
```
ou
```
sudo dnf update crystal
```

#

### OpenSUSE
Para configurar o repositório do compilador Crystal execute para OpenSUSE Tumbleweed:
```
sudo zypper ar -f https://download.opensuse.org/repositories/devel:/languages:/crystal/openSUSE_Tumbleweed/devel:languages:crystal.repo
```
Para OpenSUSE Leap 15.2:
```
sudo zypper ar -f https://download.opensuse.org/repositories/devel:/languages:/crystal/openSUSE_Leap_15.2/devel:languages:crystal.repo
```

Agora, com os repositórios devidamente configurados, execute:
```
sudo zypper --gpg-auto-import-keys install crystal
```

Para atualizar o compilador para novas versões execute para OpenSUSE Tumbleweed:
```
sudo zypper dup
```
Para OpenSUSE Leap:
```
sudo zypper up
```

Para mais informações clique <a href="https://crystal-lang.org/install/on_opensuse/">aqui!</a>

#

### Arch Linux/Manjaro e derivados
Para instalar o compilador Crystal no Arch Linux/Manjaro e derivados execute: 
```
sudo pacman -S crystal shards
```

#

### Gentoo
Primeiramente precisamos configurar algumas flags:
```
# equery u dev-lang/crystal
[ Legend : U - final flag setting for installation]
[        : I - package is installed with flag     ]
[ Colors : set, unset                             ]
 * Found these USE flags for dev-lang/crystal-0.18.7:
 U I
 - - doc      : Add extra documentation (API, Javadoc, etc). It is recommended to enable per package instead of globally
 - - examples : Install examples, usually source code
 + + xml      : Use the dev-libs/libxml2 library to enable Crystal xml module
 + - yaml     : Use the dev-libs/libyaml library to enable Crystal yaml module
```

Agora, após configurado, execute:
```
su -
emerge -a dev-lang/crystal
```

#

### FreeBSD
Para instalar o compilador Crystal no FreeBSD execute:
```
sudo pkg install -y crystal shards
```

#

### Snaps
Caso tenha tido algum problema com o gerenciador de pacotes padrão de sua distribuição, tente instalar utilizando snaps! Ainda não tem o Snap instalado? Clique <a href="https://snapcraft.io/docs/installing-snapd">aqui!</a>

Para instalar utilizando o Snap execute:
```
sudo snap install crystal --classic
```
ou
```
sudo snap install crystal --classic --edge
```

---

E aí, seu compilador Crystal já está instalado corretamente? É hora de termos o nosso primeiro contato com a linguagem Crystal!

<p align="right">
  <a href="https://github.com/lanjoni/crystal4noobs/blob/main/content/intro/helloworld.md">Próximo -> Hello World!</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/crystal4noobs#roadmap">Voltar para o menu principal</a>
</p>
