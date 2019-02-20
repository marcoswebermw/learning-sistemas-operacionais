# Gerenciando Pacotes  RPM

O CentOS trabalha com os pacotes `rpm` da família Red Hat. Que podem ser instalados pelo `rpm` para instalar binários, ou usar o `YUM` para resolver dependências automaticamente.  


## RPM  

```sh
# Opções:
-i - Instalar pacote;
-h - Mostrar progresso da instalação;
-v - Modo verboso;
-q - ;
-a - ;
-e - ;

# Instalando pacotes.
rpm -ivh /home/usuario/pacote.rpm

# Listando todos os pacotes instalados.
rpm -qa

# Verifica se determinado pacote está instalado.
rpm -qa | grep -i pacote

# Removendo pacote.
rpm -e pacote
```