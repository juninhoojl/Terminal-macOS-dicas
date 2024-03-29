# Algumas utilidades no Terminal do macOS

[José Luiz Corrêa Junior](https://github.com/juninhoojl)  - juninhopc@icloud.com

# <a name="menu"></a> Acesso rápido

* [**Bloquear mudança de tamanho do dock**](#dock-tamanho)
* [**Bloquear alterações dock**](#dock-alterar)
* [**Evitar que entre no modo suspender**](#suspender)
* [**Alterar localização do screenshots**](#screenshot-loc)
* [**Mudar formato dos screenshots**](#screenshot-formato)
* [**Gitignore global útil macOS**](#gitignore-global)
* [**Mostrar arquivos ocultos no fider**](#arquivo-oculto)
* [**Remover sombra do screenshot**](#screenshot-sombra)
* [**Habilitar a seleção de textos no quicklook**](#selecao-quicklook)
* [**Desativar o Dashboard**](#desabilitar-dashboard)
* [**Habilitar o autohide Menu Bar**](#habilitar-autohide)


## <a name="dock-tamanho"></a> Bloquear mudança de tamanho do dock [**&#x2B06; Menu**](#menu)

```
defaults write com.apple.Dock size-immutable -bool yes; killall Dock
```

###### Para reverter:

```
defaults write com.apple.Dock size-immutable -bool no; killall Dock
```

## <a name="dock-alterar"></a> Bloquear alterações dock [**&#x2B06; Menu**](#menu)

```
defaults write com.apple.Dock contents-immutable -bool yes; killall Dock
```

###### Para reverter:

```
defaults write com.apple.Dock contents-immutable -bool no; killall Dock
```


## <a name="suspender"></a> Evitar que entre no modo suspender [**&#x2B06; Menu**](#menu)

```
caffeinate
```

Ps. Isso faz com que entre no modo não suspender até que  que `control + C` (No terminal onde o comando está sendo executado) seja pressionado.


Também é possível definir um tempo específico até que se desabilite sozinho.

```
caffeinate -u -t 1800
```
(o tempo é dado em segundos, logo, 1800 -> 30 minutos)

## <a name="screenshot-loc"></a> Alterar localização do screenshots [**&#x2B06; Menu**](#menu)

Ps. Substitua <LOCATION> pelo diretório que deseja salvar as capturas de tela:

```
defaults write com.apple.screencapture location <LOCATION>; killall SystemUIServer
```

**Dica:** Para selecionar um diretório dentro do iCloud drive, arraste e solte esse diretório no terminal, e isso fará com que obtenha a localização sem precisar digitar.

**Exemplo:**

```
defaults write com.apple.screencapture location ~/Documents; killall SystemUIServer
```

## <a name="screenshot-formato"></a> Mudar formato dos screenshots [**&#x2B06; Menu**](#menu)

**Para jpg:**

```
defaults write com.apple.screencapture type jpg
```
**Para pdf:**

```
defaults write com.apple.screencapture type pdf
```

**Para tiff:**

```
defaults write com.apple.screencapture type tiff
```

**Para gif:**

```
defaults write com.apple.screencapture type gif
```

## <a name="gitignore-global"></a> Gitignore global útil macOS [**&#x2B06; Menu**](#menu)

Utilizando os seguintes comandos adicione no .gitignore_global do seu sistema:

```
echo ".DS_Store" >> ~/Git/.gitignore_global
echo "._.DS_Store" >> ~/Git/.gitignore_global
echo "**/.DS_Store" >> ~/Git/.gitignore_global
echo "**/._.DS_Store" >> ~/Git/.gitignore_global
git config --global core.excludesfile ~/Git/.gitignore_global
```

Ou simplesmente adicione as seguintes linhas no arquivo `~/Git/.gitignore_global`:

```
.DS_Store
._.DS_Store
**/.DS_Store
**/._.DS_Store
```


## <a name="arquivo-oculto"></a> Mostrar arquivos ocultos no fider [**&#x2B06; Menu**](#menu)

```
defaults write com.apple.Finder AppleShowAllFiles true; killall Finder

```

###### Para reverter:

```
defaults write com.apple.Finder AppleShowAllFiles false; killall Finder

```


## <a name="screenshot-sombra"></a> Remover sombra do screenshot [**&#x2B06; Menu**](#menu)

```
defaults write com.apple.screencapture disable-shadow -bool TRUE; killall SystemUIServer
```

###### Para reverter:

```
defaults write com.apple.screencapture disable-shadow -bool FALSE; killall SystemUIServer
```

## <a name="selecao-quicklook"></a> Habilitar a seleção de textos no quicklook [**&#x2B06; Menu**](#menu)

```
defaults write com.apple.finder QLEnableTextSelection -bool TRUE; killall Finder
```
###### Para reverter:

```
defaults write com.apple.finder QLEnableTextSelection -bool FALSE; killall Finder
```

## <a name="desabilitar-dashboard"></a> Desativar o Dashboard [**&#x2B06; Menu**](#menu)

```
defaults write com.apple.dashboard mcx-disabled -boolean TRUE; killall Dock
```

###### Para reverter:

```
defaults write com.apple.dashboard mcx-disabled -boolean FALSE; killall Dock
```
## <a name="habilitar-autohide"></a> Habilitar o autohide Menu Bar [**&#x2B06; Menu**](#menu)

```
defaults write NSGlobalDomain _HIHideMenuBar -bool true
```

###### Para reverter:

```
defaults write NSGlobalDomain _HIHideMenuBar -bool false
```


##### Conectar teclado bluetooth antes do login

This definitely seems like a FileVault problem. The necessary drivers aren’t present in the pre-boot login screen. There’s two ways this could be solved:
If such drivers are offered for FileVault, grab them from the manufacturer’s website.
Use authenticated restarts. fdesetup permits you to bypass the FileVault login screen if you supply the necessary authentication info beforehand. To initiate an authenticated restart, save all of your work, log into an administrator account, then run the below command in Terminal:

sudo fdesetup authrestart

## Nao abrir music quando apertar play

launchctl unload -w /System/Library/LaunchAgents/com.apple.rcd.plist

(Porem nao vao funcionar mais as teclas de media)

reverter:

launchctl load -w /System/Library/LaunchAgents/com.apple.rcd.plist

## Sleep porem ativo 

pmset displaysleepnow

Script:

-- Sleep Active
do shell script "pmset displaysleepnow"



## .ZSHRC

Para mostrar nome e usuario adicione a seguinte linha no ~/.zshrc

PROMPT='%{$fg[magenta]%}%n@%{$reset_color%}${ret_status} %{$fg[cyan]%}%~%{$reset_color%} $(git_prompt_info)'

Para resolver problema de permissoes:

chmod 755 /usr/local/share/zsh
chmod 755 /usr/local/share/zsh/site-functions


## Alias Sublime

sudo ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/subl


## Solucao gambiarra para permissoes do git ao altera usuario

joseluizjunior@ ~ sudo chmod -R +rwx /Users/joseluizjunior/.config
  
## sudo nano /etc/ssh/ssh_config
ENTER YOUR PASSWORD
Locate the line ‘ #   MACs hmac-md5,hmac-sha1,hmac-sha2-256,umac-64@openssh.com,hmac-ripemd160′ and remove the Hash/Pound sight from the beginning, and add the extra hashing algorithm that I’ve shown above in red. 
Locate the line ‘ #   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,aes128-cbc,3des-cbc’ and remove the Hash/Pound sight from the beginning.
Then paste the following on the end;
HostkeyAlgorithms ssh-dss,ssh-rsa
KexAlgorithms +diffie-hellman-group1-sha1,diffie-hellman-group14-sha1
  
https://www.petenetlive.com/kb/article/0001245
