# Ferramentas de Redes  

## Netstat  

Mostra portas abertas para serviços de rede.  

```sh
# Todas as portas abertas para serviços com conexões estabelecidas.
netstat

# Todas as portas abertas.
netstat -a

# Mostra o programa que abriu a porta.
netstat -p

# Filtrar por tcp.
netstat -t

# Filtrar por udp.
netstat -u

# Mostrar o número da porta no lugar do nome.
netstat -n
```  

## Lsof  

Lista todos os arquivos abertos no sistema. Mas é usada também para `ver que processo está escutando em determinada porta`.  

Provavelmente será necessário instalar essa ferramenta no sistema.  

```sh
# Baixar da mídia de instalação:
# Encontrando o pacote correto.
yum --disablerepo=* --enablerepo=c6-media provides lsof
# Instalando pacote.
yum --disablerepo=* --enablerepo=c6-media install lsof

# Baixar da internet:
yum provides lsof
yum install lsof
```  

Usando a ferramenta.  

```sh
# Verificando os processos que estão escutando na porta 53.
lsof -i :53
```  

## nmap  

Descobrir as portas abertas que podem ser acessadas pela rede.  

```sh
# USO: nmap nome_ou_ip
nmap 192.168.1.2

# Especificando as portas que queremos checar.
nmap -p 80,22 192.168.1.2

# Obtendo mais informações sobre os serviços escutados em cada porta.
nmap -sV 192.168.1.2
```  

## ping  

Envia um pequeno pacote do tipo icmp para um destino, se o destinatário receber ele devolve um pacote indicando que os dois conseguem se comunicar.  

```sh
ping www.google.com
ping 192.168.1.2
```  

## ping6  

É a versão do ping para ipv6.  

```sh
# ping6 com ipv6
ping6 2001::20c:29ff:fe78:4cb2

# ping6 em máquina local temos que determinar a interface.
ping6 -I eth0 fe80::20c:29ff:fe78:4cb1
```  

