# Verificar se há chaves SSH
***Antes de gerar uma chave SSH, você pode verificar se há outras chaves SSH.***

### Sobre chaves SSH
Você pode usar o SSH para executar operações do Git em repositórios. Para saber mais, confira [Sobre o SSH](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/about-ssh).
Se você tiver uma chave SSH existente, poderá usar a chave para autenticar as operações do Git por SSH.

### Verificar se há chaves SSH
Antes de gerar uma nova chave SSH, verifique se há chaves existentes no computador local.

> [!Note]
> O GitHub aprimorou a segurança removendo tipos de chaves mais antigos e não seguros em 15 de março de 2022.
>
> Desde essa data, não há mais suporte para as chaves DSA (`ssh-dss`). Não é possível adicionar novas chaves DSA à sua conta pessoal em GitHub.
>
> As chaves RSA (`ssh-rsa`) com um `valid_after` antes de 2 de novembro de 2021 podem continuar usando qualquer algoritmo de assinatura. As chaves RSA geradas após essa data precisam usar um algoritmo de assinatura SHA-2. Talvez alguns clientes mais antigos precisem ser atualizados para usar as assinaturas SHA-2.
> 
1. Abra Terminal.

2. Insira `ls -al ~/.ssh` para ver se as chaves SSH existentes estão presentes.
```bash
$ ls -al ~/.ssh
# Lists the files in your .ssh directory, if they exist
```
3. Verifique a listagem do diretório para verificar se você já tem uma chave SSH pública. Por padrão, os nomes de arquivos de chaves públicas com suporte para o GitHub são um dos seguintes.

* *id_rsa.pub*
* *id_ecdsa.pub*
* *id_ed25519.pub*

> [!Tip]
> Se você receber um erro indicando que `~/.ssh` não existe, você não terá um par de chaves SSH existente no local padrão. Você pode criar um novo par de chaves SSH na próxima etapa.

4. Gere uma nova chave SSH ou faça o upload de uma chave existente.

* Se você não tem um par de chave pública e privada compatível ou não deseja usar nenhum que esteja disponível, gere uma nova chave SSH.

* Se um par de chaves pública e privada existente estiver listado (por exemplo, id_rsa.pub e id_rsa) que você deseja usar para se conectar ao GitHub, você poderá adicionar a chave ao ssh-agent.

Para saber mais sobre a geração de uma nova chave SSH ou a adição de uma chave existente ao ssh-agent, confira [Gerando uma nova chave SSH e adicionando-a ao agente SSH](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).
