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

