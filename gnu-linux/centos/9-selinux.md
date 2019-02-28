# SELinux(Security Enhanced Linux)  

É um mecanismo de segurança implementado no kernel, que foi desenvolvido pela NSA. Ele cria outra camada de proteção contra acesso não-autorizado e limita os danos que um ataque pode acarretar ao sistema.  

**Estados(modos) do SELinux**  

- `Disabled` - Não faz nada;  
- `Permissive` - Faz somente o monitoramento e log das atividades do sistema, mas não restringe nada;  
- `Enforcing` - SELinux está executando, e dependendo das configurações, pode restringir a execução de alguns processos.  

**Verificar status**  

```sh
# Verificando status e modo.
sestatus

# Trocando estados(modos).
setenforce permissive
setenforce enforcing

# Desabilitando SELinux totalmente.
# Acesse o arquivo '/etc/sysconfig/selinux'.
# Ache a linha começada com 'SELINUX='.
# Ela pode ter 3 valores: permissive, enforcing e disabled.
# Coloque o valor 'disabled'. Reinicie o sistema.
SELINUX=disabled

# Verificando estados(modos).
getenforce
```  

## Contextos(Rótulos) do SELinux  

Processos, arquivos e diretórios recebem rótulos do SELinux, eles são conhecidos como `contextos`. Elementos como, um processo, arquivo ou diretório com determinado contexto poderá ou não executar determinadas ações. Cada elemento desses pode conter contextos diferentes.  

```sh
# Verificando contextos.
ls -Z /home/
ls -Z /etc/passwd
ls -Zd /etc/passwd

# Verificando contextos de processos em execução.
ps -Z

# Mudando um contexto com 'chcon'.
chcon -t httpd_sys_content_t /home/test.txt
```  

## Valores Booleanos  

O SELinux mantém valores booleanos que influenciam o comportamento do sistema.  

```sh
# Obter lista de valores booleanos.
getsebool -a

# Obter valor booleano específico.
getsebool abrt_anon_write

# Alterando valores booleanos provisoriamente.
setsebool abrt_anon_write on

# Alterando valores booleanos permanentemente.
setsebool -P abrt_anon_write on
```  

## Ferramenta para gerenciamento do SELinux  

Uma ferramenta útil para gerenciar o SELinux é o `semanage`. Ela geralmente não vem instalada com o sistema. Para usá-la é necessário instalar o pacote `policycoreutils-python`.  

```sh
# Lista de diferentes contextos.
semanage fcontext -l

# Lista dos booleanos SELinux e uma pequena descrição.
semanage boolean -l
```