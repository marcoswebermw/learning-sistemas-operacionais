# Utilitários Visualização de Arquivos  

```sh
# Visualizar conteúdo de um arquivo.
cat arquivo
cat arquivo1 > arquivo2 # Redirecionando saída para outro arquivo.

# Paginação.
more arquivo.txt # A paginação não permite voltar.
less arquivo.txt # A paginação permite voltar.
cat arquivo.txt | more
cat arquivo.txt | less

# Exibir linhas iniciais de um arquivo.
head /var/log/messages # Exibe as 10 primeiras linhas por padrão.
head /var/log/messages -n 5 # Exibe só as 5 primeiras linhas.

# Exibir linhas finais de um arquivo.
tail /var/log/messages # Exibe as 10 ultimas linhas por padrão.
tail /var/log/messages -n 2 # Exibe somente as 2 ultimas linhas.
tail -f /var/log/messages # Exibe as últimas linhas em tempo real(CTRL+C para sair).

# Filtrando conteúdo de arquivo ou saída de algum comando.
cat arquivo | grep palavra_chave
cat /etc/passwd | grep root # Mostra somente o root.
cat -v /etc/passwd | grep root # Mostra todos menos o root.
cat -v /etc/passwd | grep "#" # Não mostra as linhas comentadas.
cat /etc/passwd | grep -i "#" # Case Insensitive.


```  