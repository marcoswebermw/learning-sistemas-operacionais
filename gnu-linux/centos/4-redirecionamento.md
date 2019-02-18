# Redirecionamento  

```sh
# Redirecionando uma entrada para uma saída.
cat /etc/passwd > /home/usuario/arquivo.txt  # Sobrescreve.
cat /etc/passwd >> /home/usuario/arquivo.txt # Anexa.

# Usando o 'pipe - |'.
echo /etc/passwd | grep root
cat /etc/group | less

# Redirecionando e vendo o redirecionamento na tela simultaneamente.
cat /etc/passwd | tee /home/usuario/arquivo.txt


```  