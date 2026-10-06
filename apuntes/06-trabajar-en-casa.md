# Trabajar desde casa

## 1. Instalar lo necesario

Linux (Ubuntu/Debian):

```bash
sudo apt update
sudo apt install git gh
curl -LsSf https://astral.sh/uv/install.sh | sh
source ~/.bashrc
```

Windows: instalar [Git for Windows](https://git-scm.com/download/win) y [GitHub CLI](https://cli.github.com/), y para uv:

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Comprobar:

```bash
git --version
gh --version
uv --version
```

## 2. Configurar Git y GitHub (solo la primera vez)

```bash
git config --global user.name "Diego Gil"
git config --global user.email "diegogildam@gmail.com"
git config --global init.defaultBranch main
gh auth login      # GitHub.com > HTTPS > login con el navegador
gh auth setup-git  # para que git use la sesión de gh
```

## 3. Bajar este repo de apuntes

Es privado, así que hace falta haber hecho `gh auth login` antes:

```bash
gh repo clone diegoalegil/dpl-2dam
cd dpl-2dam
```

## 4. Bajar el repo de clase y levantar la web

```bash
git clone https://github.com/monium/gitanddocs.git
cd gitanddocs
uv sync                  # descarga Python 3.14 si no lo tienes e instala Zensical
uv run zensical serve    # abrir http://127.0.0.1:8000
```

Si se trabaja con fork, se clona el fork y se añade `upstream` (ver [03-git-github.md](03-git-github.md)).

## 5. Rutina al empezar y al terminar

Al empezar:

```bash
cd dpl-2dam && git pull
cd ../gitanddocs && git switch main && git pull     # o: git fetch upstream && git merge upstream/main
```

Al terminar:

```bash
git status
git add .
git commit -m "Qué he hecho"
git push
```

Así lo que haga en casa está luego en clase y al revés. Lo más importante es no olvidar el `push` al acabar ni el `pull` al empezar.
