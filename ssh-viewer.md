# Verificar se há chaves SSH
1. Abra Terminal.

2. Insira `ls -al ~/.ssh` para ver se as chaves SSH existentes estão presentes.
```bash
$ ls -al ~/.ssh
# Lists the files in your .ssh directory, if they exist
```
3. Verifique a listagem do diretório para verificar se você já tem uma chave SSH pública. Por padrão, os nomes de arquivos de chaves públicas com suporte para o GitHub são um dos seguintes.

* _id_rsa.pub_
* _id_ecdsa.pub_
* _id_ed25519.pub_

### Dica

Se você receber um erro indicando que `~/.ssh` não existe, você não terá um par de chaves SSH existente no local padrão. Você pode criar um novo par de chaves SSH na próxima etapa.

4. Gere uma nova chave SSH ou faça o upload de uma chave existente.

* Se você não tem um par de chave pública e privada compatível ou não deseja usar nenhum que esteja disponível, gere uma nova chave SSH.

* Se um par de chaves pública e privada existente estiver listado (por exemplo, id_rsa.pub e id_rsa) que você deseja usar para se conectar ao GitHub, você poderá adicionar a chave ao ssh-agent.

Para saber mais sobre a geração de uma nova chave SSH ou a adição de uma chave existente ao ssh-agent, confira [Gerando uma nova chave SSH e adicionando-a ao agente SSH](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).
