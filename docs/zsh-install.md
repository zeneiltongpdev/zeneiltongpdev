# Projeto ZSH Terminal Linux e/ou WSL2
## 1️⃣ Instalar o Zsh
Primeiro, instale o Zsh e verifique a versão instalada:
```
sudo apt update && sudo apt install -y zsh
zsh --version
```
Agora, defina o Zsh como shell padrão:
```
chsh -s $(which zsh)
```
Reinicie o terminal ou rode zsh para começar a usá-lo.

## 2️⃣ Instalar o Oh My Zsh (Gerenciador de Configuração)
O Oh My Zsh facilita a gestão do Zsh e seus plugins. Instale com:
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
Se não tiver curl, instale com:
```
sudo apt install curl -y
```
## 3️⃣ Instalar Plugins Essenciais
Aqui estão os melhores plugins para melhorar a experiência no terminal:

**📌 1. zsh-autosuggestions (Sugestões de comandos)**
```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
**📌 2. zsh-syntax-highlighting (Destaque de sintaxe)**
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
**📌 3. fzf (Auto-complete e busca avançada)**
```
sudo apt install fzf -y
```
**📌 4. Powerlevel10k (Tema super customizável)**
```
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k
```
Agora, edite o arquivo **.zshrc** para realizar as configurações:

## 4️⃣ Ativar os Plugins no .zshrc
Abra o arquivo .zshrc:
```
nano ~/.zshrc
```
E altere as seguintes linhas: `#ZSH_THEME="..."` para:
```
ZSH_THEME="powerlevel10k/powerlevel10k"
```
Depois Encontre a linha que começa com `plugins=(...)` e modifique para incluir os plugins:
```
plugins=(git zsh-autosuggestions zsh-syntax-highlighting fzf)
```
Para Salvar, aperte **(Ctrl + X, Y, Enter)** e aplique as mudanças com o comando abaixo:
```
source ~/.zshrc
```
O Powerlevel10k pedirá para ser configurado. Siga o assistente para escolher um estilo.

Para futuras configurações do **Powerlevel10k**
###

🎉 Tudo pronto!
Agora você tem um terminal rápido, bonito e eficiente com Zsh! 🚀

## Instalando o colorls?

O colorls deixa a saída do ls muito mais bonita, com ícones e cores diferenciadas. Aqui está o passo a passo para instalar e configurar corretamente. 🚀

## 5️⃣ Instalando as Dependências
Antes de instalar o colorls, precisamos do Ruby e algumas bibliotecas extras:
```
sudo apt update && sudo apt install -y ruby ruby-dev build-essential
```
Agora, verifique a versão do Ruby para garantir que está instalado corretamente:
```
ruby -v
```
## 6️⃣ Instalar o colorls
Agora, instale o colorls via gem:
```
sudo gem install colorls
```
Para verificar se foi instalado corretamente:
```
colorls --help
```
Se aparecer um erro sobre permissão, tente:
```
sudo gem install colorls --no-document
```
## 7️⃣ Instalar Nerd Fonts (Para Ícones)
O `colorls` usa ícones que só aparecem corretamente se você tiver uma Nerd Font instalada. Aqui está como instalar a JetBrains Mono Nerd Font:
```
mkdir -p ~/.local/share/fonts && cd ~/.local/share/fonts
wget https://github.com/ryanoasis/nerd-fonts/releases/latest/download/JetBrainsMono.zip
unzip JetBrainsMono.zip && rm JetBrainsMono.zip
fc-cache -fv
```
Depois, vá até as configurações do seu terminal e mude a fonte para `JetBrains Mono Nerd Font.`

## 8️⃣ Instalando o Tree
O tree é um utilitário simples para exibir diretórios em formato de árvore. Instale com:
```
sudo apt update && sudo apt install -y tree
```
Depois, verifique se a instalação foi bem-sucedida:
```
tree --version
```
## 9️⃣ Criar Alias para Facilitar o Uso LS & TREE
Abra seu arquivo **.zshrc** para editar:
```
nano ~/.zshrc
```
E adicione as seguintes linhas no final do arquivo:
```
alias ls='ls --color=auto'
alias ll='ls -l'
alias lla='ls -la'
alias la='ls -A'
# alias l='ls -F'
command -v lsd > /dev/null && alias ls='lsd --group-dirs first' && \
	alias tree='lsd --tree'
command -v colorls > /dev/null && alias ls='colorls --sd --gs' && \
	alias tree='colorls --tree'
```
###
```
source ~/.zshrc
```
## 🔟 Testar o colorls + Tree! 🎨
Agora, teste os comandos:
```
ls
ll
lt
```
Se os ícones não aparecerem corretamente, tente rodar:
```
colorls -l --sd
```
**Como Usar o Tree? Aqui estão alguns comandos úteis:**

Mostrar a estrutura de diretórios:
```
tree
```
Mostrar arquivos ocultos também (-a):
```
tree -a
``` 
Limitar a profundidade da árvore (-L 2 para exibir até 2 níveis de profundidade):
```
tree -L 2
```
Exibir permissões e tamanhos (-p para permissões, -h para tamanho legível):
```
tree -p -h
```
Salvar a saída em um arquivo de texto:
```
tree > estrutura.txt
```
Se ainda não aparecerem, verifique se a Nerd Font está ativada no seu terminal.

## 🎉 Pronto! Agora seu terminal está mais bonito e organizado com ZSH + Powerlevel10k + Colorls + Tree !🚀😃

![Shell](https://private-user-images.githubusercontent.com/8356174/416450967-ba51d68d-b572-4132-9790-32883a2a9f32.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDkyNzIwNTMsIm5iZiI6MTc0OTI3MTc1MywicGF0aCI6Ii84MzU2MTc0LzQxNjQ1MDk2Ny1iYTUxZDY4ZC1iNTcyLTQxMzItOTc5MC0zMjg4M2EyYTlmMzIucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI1MDYwNyUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNTA2MDdUMDQ0OTEzWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MTRmNTg2Mzk3MjM5ZmUwY2JiYjI3MDM3MTMyMGVkOTFmMzRiZGY2MTBjODgzYjQ5OTAzYzYxMDhmZGNkN2Q0MiZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.W_FAsD-hAJfp00PdCYVvkhzeTDb2j7hClBOtiLIU94E)
