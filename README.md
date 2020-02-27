# Pyenv + Pipenv + Vim/Neovim

How I use Pyenv + Pipenv + Vim/Neovim for my daily projects.

## Pyenv config

```sh
$ pyenv local 3.7.4
```

We check with

```sh
$ pyenv version
3.7.4 (set by /home/cjadeveloper/.../my-project/.python-version)
```

## Pipenv 

### Create a new project using Python 3.7.4, specifically

If we open a terminal and write `pyenv which python`, it will return the full path to the current python executable 

```sh
$ pyenv which python
/home/cjadeveloper/.pyenv/versions/3.7.4/bin/python
```

If we are on could use this information 

```sh
$ pipenv --python $(pyenv which python)
```
