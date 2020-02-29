# Algumas utilidades no Terminal do macOS

###### juninhoojl

## Bloquear mudança de tamanho do dock

```
defaults write com.apple.Dock size-immutable -bool yes; killall Dock
```

###### Para reverter:

```
defaults write com.apple.Dock size-immutable -bool no; killall Dock
```

## Bloquear alterações dock

```
defaults write com.apple.Dock contents-immutable -bool yes; killall Dock
```

###### Para reverter:

```
defaults write com.apple.Dock contents-immutable -bool yes; killall Dock
```


## Evitar que entre no modo suspender

```
caffeinate
```

Ps. Isso faz com que entre no modo não suspender até que  que `control + C` (No terminal onde o comando está sendo executado) seja pressionado.


Também é possível definir um tempo específico até que se desabilite sozinho.

```
caffeinate -u -t 1800
```
(o tempo é dado em segundos, logo, 1800 -> 30 minutos)

## Alterar localização do screenshots

Ps. Substitua <LOCATION> pelo diretório que deseja salvar as capturas de tela:

```
defaults write com.apple.screencapture location <LOCATION>; killall SystemUIServer
```

**Dica:** Para selecionar um diretório dentro do iCloud drive, arraste e solte esse diretório no terminal, e isso fará com que obtenha a localização sem precisar digitar.

**Exemplo:**

```
defaults write com.apple.screencapture location ~/Documents; killall SystemUIServer
```

## Mudar formato dos screenshots

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

## Gitignore global útil macOS

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


## Mostrar arquivos ocultos no fider:

```
defaults write com.apple.Finder AppleShowAllFiles true; killall Finder

```

###### Para reverter:

```
defaults write com.apple.Finder AppleShowAllFiles false; killall Finder

```


## Remover sombra do screenshot:

```
defaults write com.apple.screencapture disable-shadow -bool TRUE; killall SystemUIServer
```

###### Para reverter:

```
defaults write com.apple.screencapture disable-shadow -bool FALSE; killall SystemUIServer
```

## Habilitar a seleção de textos no quicklook 


```
defaults write com.apple.finder QLEnableTextSelection -bool TRUE; killall Finder
```
###### Para reverter:

```
defaults write com.apple.finder QLEnableTextSelection -bool FALSE; killall Finder
```

## Desativar o Dashboard

```
defaults write com.apple.dashboard mcx-disabled -boolean TRUE; killall Dock
```

###### Para reverter:

```
defaults write com.apple.dashboard mcx-disabled -boolean FALSE; killall Dock
```
