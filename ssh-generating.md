# Gerando uma nova chave SSH e adicionando-a ao agente SSH

***Depois de verificar a existência de chaves SSH, é possível gerar uma nova chave SSH para autenticação e adicioná-la ao ssh-agent.***

### Sobre frases secretas da chave SSH
Você pode acessar e gravar dados nos repositórios em GitHub usando o protocolo SSH (Secure Shell Protocol). Ao se conectar por meio do SSH, você se autentica usando um arquivo de chave privada no computador local. Para saber mais, confira [Sobre o SSH](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/about-ssh).

Ao gerar uma chave SSH, você pode adicionar uma frase secreta para proteger ainda mais a chave. Sempre que você usar a chave, deverá inserir a frase secreta. Se sua chave tiver uma frase secreta e você não quiser inserir a frase secreta sempre que usar a chave, poderá adicionar sua chave ao agente SSH. O agente SSH gerencia suas chaves SSH e lembra sua frase secreta.

Se você ainda não tem uma chave SSH, você deve gerar uma nova chave SSH para usar para a autenticação. Se você não tem certeza se já tem uma chave SSH, você pode verificar se há chaves existentes. Para saber mais, confira [Verificar se há chaves SSH](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys).

Se você deseja usar uma chave de segurança de hardware para efetuar a autenticação no GitHub, deverá gerar uma nova chave SSH para a sua chave de segurança de hardware. Você deve conectar a sua chave de segurança de hardware ao seu computador ao efetuar à sua autenticação com o par de chaves. Para obter mais informações, confira as [notas sobre a versão do OpenSSH 8.2](https://www.openssh.com/txt/release-8.2).

### Gerar uma nova chave SSH
Você pode gerar uma nova chave SSH no computador local. Depois de gerar a chave, você pode adicionar a chave pública à sua conta em GitHub.com para habilitar a autenticação para operações do Git no SSH.

> [!Note]
> Observação*
> O GitHub aprimorou a segurança removendo tipos de chaves mais antigos e não seguros em 15 de março de 2022.
>
> Desde essa data, não há mais suporte para as chaves DSA (`ssh-dss`). Não é possível adicionar novas chaves DSA à sua conta pessoal em GitHub.
>
> As chaves RSA (`ssh-rsa`) com um `valid_after` antes de 2 de novembro de 2021 podem continuar usando qualquer algoritmo de assinatura. As chaves RSA geradas após essa data precisam usar um algoritmo de assinatura SHA-2. Talvez alguns clientes mais antigos precisem ser atualizados para usar as assinaturas SHA-2.

1. Abra Terminal.

2. Cole o texto abaixo, substituindo o email usado no exemplo pelo seu endereço de email do GitHub.
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
> [!Note]
> Observação
> 
> Se estiver usando um sistema herdado que não dá suporte ao algoritmo Ed25519, use:
> ```bash
> ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
> ```

Isto cria uma nova chave SSH, usando o nome de e-mail fornecido como uma etiqueta.
```bash
> Generating public/private ALGORITHM key pair.
```
Quando for solicitado a inserir um arquivo para salvar a chave, pressione Enter para aceitar o local padrão do arquivo. Observe que, se você criou chaves SSH anteriormente, ssh-keygen pode pedir que você reescreva outra chave. Nesse caso, recomendamos criar uma chave SSH personalizada. Para fazer isso, digite o local do arquivo padrão e substitua id_ALGORITHM pelo nome da chave personalizada.
```bash
> Enter a file in which to save the key (/home/YOU/.ssh/id_ALGORITHM):[Press enter]
```
No prompt, digite uma frase secreta segura. Para saber mais, confira [Trabalhar com frase secreta da chave SSH](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/working-with-ssh-key-passphrases).
```bash
> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]
```
### Adicionar sua chave SSH ao ssh-agent
Antes de adicionar uma nova chave SSH ao agente para gerenciar suas chaves, você deve verificar as chaves SSH existentes e gerado uma nova chave SSH.

1. Inicie o ssh-agent em segundo plano.
```bash
$ eval "$(ssh-agent -s)"
> Agent pid 59566
```
Dependendo do seu ambiente, talvez seja necessário usar um comando diferente. Por exemplo, talvez seja necessário usar o acesso raiz executando `sudo -s -H` antes de iniciar o ssh-agent ou usar `exec ssh-agent bash` ou `exec ssh-agent zsh` para executar o ssh-agent.

2. Adicione sua chave SSH privada ao ssh-agent.

Se você criou sua chave com um nome diferente ou está adicionando uma chave existente que tenha outro nome, substitua *id_ed25519* no comando pelo nome do arquivo de chave privada.
```bash
ssh-add ~/.ssh/id_ed25519
```
3. Adicione a chave pública SSH à sua conta em GitHub. Para saber mais, confira [Adicionar uma nova chave SSH à sua conta do GitHub](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).

### Gerar uma nova chave SSH para uma chave de segurança de hardware
Se você estiver usando macOS ou Linux, Talvez você precise atualizar seu cliente SSH ou instalar um novo cliente SSH antes de gerar uma nova chave SSH. Para saber mais, confira [Erro: Tipo de chave desconhecido](https://docs.github.com/pt/authentication/troubleshooting-ssh/error-unknown-key-type).

1. Insira sua chave de segurança de hardware no seu computador.

2. Abra Terminal.

3. Cole o texto abaixo, substituindo o endereço de email usado no exemplo pelo endereço de email associado à sua conta do GitHub.
```bash
ssh-keygen -t ed25519-sk -C "your_email@example.com"
```
> [!NOTE]
> Se ocorrer uma falha no comando e você receber o erro invalid format ou feature not supported,, você poderá estar usando uma chave de segurança de hardware que não dá suporte ao algoritmo Ed25519. Insira o comando a seguir.
> `ssh-keygen -t ecdsa-sk -C "your_email@example.com"`
4. Quando solicitado, toque no botão da sua chave de segurança de hardware.

5. Quando for solicitado a "Insira um arquivo para salvar a chave", pressione Enter para aceitar o local padrão do arquivo.
```bash
> Enter a file in which to save the key (/home/YOU/.ssh/id_ed25519_sk):[Press enter]
```
6. Quando precisar digitar uma frase secreta, pressione ENTER.
```bash
> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]
```
7. Adicione a chave pública SSH à sua conta em GitHub. Para saber mais, confira [Adicionar uma nova chave SSH à sua conta do GitHub](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).
