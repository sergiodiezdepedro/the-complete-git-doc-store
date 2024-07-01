# The Complete Git Doc Store Notebook

[git-scm.com](https://git-scm.com/). La página oficial de Git.

## Instalación en macOS

```bash
brew install git
```

Comprobamos la versión instalada de Git                 .

```bash
git -v
```

```bash
git --version
```

Para que el sistema utilice este git y no el que incluye Apple cuando se se instalan las [`Command Line Tools`](https://www.maketecheasier.com/install-command-line-tools-without-xcode/) hay que teclear en la terminal:

```bash
export PATH=/usr/local/bin:$PATH
git --version
```
## Configurar .gitconfig

```bash
git config --global user.name "Sergio Díez de Pedro"
```

```bash
git config --global user.email "sergio.d.depedro@gmail.com"
```

## Inicializar Git en un directorio

```bash
git init
```

## Configurar globalmente la rama inicial por defecto

```bash
git config --global init.defaultBranch main
```


