# Gerenciando Pacotes - YUM(Yellowdog Updater, Modified)  

O `YUM` resolve as dependências de um pacote automaticamente, ao contrario do `rpm`.  

A busca de pacotes, por padrão, é feita pelo YUM no repositório `http:/mirrorlist.centos.org`. Mas é possível alterá-la, principalmente quando não existe acesso à Internet e gostariamos de fazer a busca por pacotes através de um DVD.  

O diretório `/etc/yum.repos.d` mantém um conjunto de arquivos que estão associados com repositórios do CentOS.  

O CentOS 6 já tem um repositório associado para fazer busca em DVDs que está no arquivo `CentOS-Media.repo` internamente chamado de `c6-media`, porém, por padrão vem desabilitado. Para usá-lo exclusivamente é necessário desabilitar os outros repositórios e habilitá-lo. Isso pode ser feito editando o arquivo manualmente ou através de comandos pelo próprio YUM. O DVD tem que estar no drive e montado no diretório `/media/cdrom/`.  

> Para montar o DVD use: `mount /dev/cdrom /media/cdrom/` 

O CentOS 7 não vem com esse arquivo de repositório, portanto é necessário criá-lo, editá-lo, habilitá-lo e montar o DVD também.  

## YUM Opções  

```sh
# Listar repositórios
yum repolist
yum --disablerepo=* --enablerepo=c6-media list # Habilitando somente DVDs no CentOS6.
yum --disablerepo=* --enablerepo=c7-media list # Habilitando somente DVDs no CentOS7.

# Listar grupos de pacotes
yum grouplist
yum grouplist hidden # É necessário no CentOS 7 que não exibe todos os grupos por padrão.

# Obter informações de um grupo
yum groupinfo "GNOME Desktop"

# Listar pacotes
yum list
yum list pacote

# Instalar pacotes
yum install pacote
yum install pacote -y # Confirmação automatica.

# Instalar grupo de pacotes
yum groupinstall "GNOME Desktop"

# Remover um grupo de pacotes
yum groupremove "GNOME Desktop"

# Instalar grupo de pacotes, inclusive os opcionais recomendados.
yum  --setopt=group_package_types=optional groupinstall -y
```  
-----------------------------  

## CentoOS 6  

Configurando repositório no CentOS6:  

```sh
# Monte o DVD.
mkdir /media/cdrom
mount /dev/cdrom /media/cdrom/

# Desabilite todos repos e habilite o c6-media.
# Serve para exibir apenas pacotes contidos no DVD.
yum --disablerepo=* --enablerepo=c6-media list
```  

Intalando o comando `man` no sistema, que não vem na instalação mínima.  

```sh
# Localizando o pacote onde se encontra o 'man'.
yum provides man

# Instalando o pacote man.
yum install man
```  

Instalando ambiente gráfico.  

```sh
# Instala grupos de pacotes relacionados ao ambiente gráfico.
yum install "Desktop Platform" "X Window System" "Fonts" -y

# Use o Runlevel abaixo para trocar para o ambiente gráfico.
init 5
```

-----------------------------  

## CentoOS 7  

Configurando repositório no CentOS7:  

```sh
# Crie o arquivo CentOS-Media.repo.
touch /etc/yum.repos.d/CentOS-Media.repo

# Insira as linhas abaixo no arquivo CentOS-Media.repo.
[c7-media]
name=CentOS-$releasever - Media
baseurl=file:///media/cdrom/
gpgcheck=0
enabled=0

# Monte o DVD.
mkdir /media/cdrom
mount /dev/cdrom /media/cdrom/

# Teste se os pacotes desse repo são listados.
# Serve para exibir apenas pacotes contidos no DVD.
yum --disablerepo=* --enablerepo=c7-media list
```  

Instalando ambiente gráfico.  

```sh
# Instala grupos de pacotes relacionados ao ambiente gráfico.
yum install "X Window System" "Gnome Desktop" -y

# Use o comando abaixo para trocar para o ambiente gráfico.
startx
```