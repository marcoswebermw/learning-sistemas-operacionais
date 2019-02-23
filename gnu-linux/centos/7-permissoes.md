# Permissões  

Os arquivos podem ser acessados de acordo com permissões de quem quer acessá-los têm sobre eles. 

Essas permissões podem ser gerenciadas com alguns comandos existentes em sistemas Unix-like.  

## Mudando permissões com `chmod`  

**Permissões**  

- `r` - Leitura;  
- `w` - Escrita;  
- `x` - Execução;  

**Tipos de Ações**  

- `+` - Adicionar permissão;  
- `-` - Remover permissão;  

**Quem sofrerá Ações**  

- `u` - Owner(Dono);  
- `g` - group(Grupo);  
- `o` - Others(Outros);  

Exemplos:  

```sh
chmod o+w /etc/passwd # Adicionando permissão de escrita para outros usuários.
chmod o-w /etc/passwd # Removendo permissão de escrita para outros usuários.
```  