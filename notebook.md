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

## git log

[Este comando](https://chatgpt.com/share/4f0c105b-eeed-455c-b6d8-55e6809a5c9b) muestra la historia de commits del repositorio.

## git checkout

`git checkout` is a versatile command used in Git to switch between different branches or to restore working tree files. Here's a detailed explanation of its uses:

**Switching Branches**
To switch to an existing branch:

```bash
git checkout branch_name
```

For example, if you want to switch to a branch called feature-branch:

```bash
git checkout feature-branch
```

**Creating and Switching to a New Branch**

You can create a new branch and switch to it in one command:

```bash
git checkout -b new_branch_name
```

For example, to create and switch to a branch called new-feature:

```bash
git checkout -b new-feature
```

**Restoring Files**

You can use git checkout to restore a specific file to its state in another branch or commit:

```bash
git checkout branch_name -- path/to/file
```
For example, to restore a file called `example.txt` from the main branch:

```bash
git checkout main -- example.txt
```

**Checking Out a Specific Commit**

You can also check out a specific commit by its hash:

```bash
git checkout commit_hash
```
For example, to check out a commit with the `hash a1b2c3d4`:

```bash
git checkout a1b2c3d4
```

### Deprecated in Favor of `git switch` and `git restore`

As of Git 2.23, `git switch` and `git restore` commands were introduced to separate the functionalities of git checkout:

- `git switch` is used to switch branches.
- `git restore` is used to restore files.

Examples:

Switching branches with git switch:

```bash
git switch branch_name
```

Creating and switching to a new branch with git switch:

```bash
git switch -c new_branch_name
```
Restoring files with git restore:

```bash
git restore path/to/file
```

Restoring a file from another branch with git restore:

```bash
git restore --source branch_name -- path/to/file
```
Using these newer commands can make the intent of your Git operations clearer.

## git alias

```bash
git config --global alias.lorem "comandos git"
```

Ejemplo:

```bash
git config --global alias.lg "log --graph --decorate --all --oneline"
```

## git diff

[Este comando](https://chatgpt.com/share/4f219943-a59c-461d-9e2a-f9158df6ce55) muestra las diferencias entre varios commits, ramas, archivos, o el directorio de trabajo y el index (área de stage).

