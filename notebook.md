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

## git reset --hard

[El comando](https://chatgpt.com/share/78bcd537-b939-47aa-9a99-d5559de28ba2) se utiliza para resetear la rama actual a un estado específico, descartando todos los cambios locales y commits.

```bash
git reset --hard <commit>
```

- `<commit>`. Puede ser el hash de un commit, el nombre de una rama, una etiqueta o cualquier otra referencia a un commit específico de la historia.

- `--hard`: Esta opción significa que el directorio de trabajo y el index serán borrados para ajustarse a un commit especificado. Todos los cambios de los archivos con seguimiento del directorio de trabajo serán descartados.

Dado el poder de este comando, hay que tener en cuenta que puede haber pérdida de datos en local, es irreversible y puede tener impactos en los colaboradores de un repositorio compartido.

**IMPORTANTE**: el comando también actúa hacia delante, ya que permite volver al final de los commits que se habían borrado localmente y recuperar todo hasta el `HEAD` más avanzado.

## git revert

[Esta orden](https://chatgpt.com/share/ad683fd0-1efd-4fc7-800e-a1d2e7124935) se emplea para crear un nuevo commit que deshace los cambios introducidos por un commit anterior.

A diferencia de `git reset`, que puede modificar la historia del commit, `git revert` es una operación segura para repositorios compartidos porque no altera la historia existente.

## git reflog

Es [un comando](https://chatgpt.com/share/861f2900-e9e1-4db5-9475-792c3760a7a6) poderoso que muestra un registro de todas la referencias (commits) al que el repositorio local apunta. Esto incluye, no sólo commits, sino otros cambios como actualización de ramas y resets y similares. Básicamente, permite ver la historia del `HEAD` y otras referencias.

Asimismo, habilita la posibilidad de recuperar commits perdidos y deshacer cambios.

Ejemplo de output:

```bash
b0a21f3 (HEAD -> main) HEAD@{0}: commit: Add new feature
7c829d5 HEAD@{1}: commit: Fix bug in feature
a72e98b HEAD@{2}: commit: Update README
2c7a6f1 HEAD@{3}: checkout: moving from main to feature-branch
4f6a1e0 (feature-branch) HEAD@{4}: commit: Start feature-branch
e3cbf6f HEAD@{5}: checkout: moving from main to e3cbf6f
```

## git tag

[Esta instrucción](https://chatgpt.com/share/94f79314-8e7d-4bf8-9d2e-625a2dffe858) se utiliza para crear, listar, borrar o verificar **etiquetas (tags)** en el repositorio. 

Las etiquetas son referencias que marcan puntos específicos en la historia dle repositorio, usualmente para destacar puntos de *releases* (v1.0, v2.0, por ejemplo).

## Diferencias entre `git add .`, `git add -u` y `git add -A`

- `git add .`: Stages new and modified files in the current directory and its subdirectories but does not stage deletions.
- `git add -u`: Stages modifications and deletions but does not stage new files.
- `git add -A`: Stages all changes (new files, modifications, and deletions) in the working directory.

## git branch, git switch

La [gestión de ramas](https://chatgpt.com/share/71b054b1-654c-4b7d-bfac-e98b83d86d73) es una característica fundamental de Git. 

**Comandos básicos**

- Crear una nueva rama:
```bash
git branch <branch_name>
```
- Listar todas las ramas del repositorio:
```bash
git branch
```
- Cambiar a una rama
```bash
git switch <branch_name>
```
- Crear una nueva rama y cambiarse a ella
```bash
git switch -c <branch_name>
```
- Renombrar la rama actual
```bash
git branch -m <new_branch_name>
```

Borrar una rama tiene algunas especificidades. Revisar la información que aporta el link de esta sección al respecto. 





