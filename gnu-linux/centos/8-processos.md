# Processos  

Aqui são mostrados comandos para verificar os processos em execução no sistema.  

No CentOS6 o processo inicial é o `init`. No CentOS7 o processo inicial é o `systemd`.  


## Comando `ps`  

O comando ps sem parâmetros vai exibir todos os processos associados com o terminal atual. Ele mostrará informações como os comandos que geraram o processo, UID, PID(id do processo), terminal, tempos de execução.  

**Opções**  

- `-e` - Todos os processos;  
- `-f` - Mais detalhes como tempo de início do processo, PPID(id do processo pai do processo);  

```sh
ps
ps -e 
ps -ef
ps aux
```  

## Comando `pstree`  

## Comando `top`  

