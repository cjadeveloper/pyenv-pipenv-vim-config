# Pyenv + Pipenv + Neovim

How I use Pyenv + Pipenv + Neovim for my daily projects.

## Pyenv config

In our project directory, we could make 

```bash
$ pyenv local 3.7.4
```

We check with

```bash
$ pyenv version
3.7.4 (set by /home/cjadeveloper/.../my-project/.python-version)
```

## Pipenv 

### Create a new project using Python 3.7.4, specifically

If we open a terminal and write `pyenv which python`, it will return the full path to 
the current python executable 

```bash
$ pyenv which python
/home/cjadeveloper/.pyenv/versions/3.7.4/bin/python
```

We If we could use this information 

In bash or zsh to do:

```bash
$ pipenv --python $(pyenv which python)
Creating a virtualenv for this project…
Pipfile: /home/cjadeveloper/.../my-project/Pipfile
Using /home/cjadeveloper/.pyenv/versions/3.7.4/bin/python (3.7.4) to create virtualenv…
...
```

In fish:

```fish
> pipenv --python (pyenv which python)
Creating a virtualenv for this project…
Pipfile: /home/cjadeveloper/.../my-project/Pipfile
Using /home/cjadeveloper/.pyenv/versions/3.7.4/bin/python (3.7.4) to create virtualenv…
...
```

### Install Neovim Python Packages and fancy interactive superpower terms

1. You will need NeoVim 0.3 or newer

2. Install the required dependencies:

```bash
sudo apt install git curl python3-pip exuberant-ctags ack-grep
```

3. Inside the project directory, install dependencies with pipenv

```bash
pipenv install --dev neovim flake8 pylint isort msgpack pynvim bpython ipython
```

4. Download the [config file](https://gist.github.com/cjadeveloper/7aea22b64bb2419c44d55c304c3246ae) and  save it as `~/.config/nvim/init.vim` (use that exact path and name).

5. Open Neovim with `pipenv run nvim .` and it will it continue the installation by 
itself. Wait for it finish and done!

6. Then, when Neovim already works, we could activate the venv with `pipenv shell --fancy` 
inside our projects directory and open it with `nvim .`

> Note: The `--fancy` option is necessary in case we use fish together with some oh-my-fish theme and the prompt breaks. Just as pointed out [here](https://github.com/sentriz/fish-pipenv/issues/18)

### Optional: Pipenvwrapper

[Pipenvwrapper](https://github.com/Peibolvig/pipenvwrapper) is a shell functions 
similar to virtualenvwrapper but using Pipenv as backend.

If we use Pipenvwrapper, we could write `workon` (or` useenv` depends on how we 
configure it) and use a specific virtualenv or list all the available ones if none is
provided. With this we can activate the venv and go directly to the project folder from
wherever we are.

## References

- [Vim Cheat Sheet](https://vim.rtorr.com/)
- [pipenv](https://pipenv.kennethreitz.org/en/latest/#)
- [pyenv](https://github.com/pyenv/pyenv)
- [fisa vim config](http://vim.fisadev.com/)
- [Creating a new file or directory in Vim using NERDTree](https://sookocheff.com/post/vim/creating-a-new-file-or-directoryin-vim-using-nerdtree/)
