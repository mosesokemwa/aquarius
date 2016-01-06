# pep8
**it helps by linting out python code making a developers work easier**

## installing ```pep8```

```markdown
$ pip install pep8
$ pip install --upgrade pep8
$ pip uninstall pep8
```

**You might want to use `sudo` to gain access to root**

# Flake8
Flake8 is a wrapper around these tools:

```
PyFlakes
pep8
```

Ned Batchelder's McCabe script Flake8 runs all the tools by launching the single flake8 script. It displays the warnings in a per-file, merged output.

It also adds a few features:

files that contain this line are skipped:

`# flake8: noqa`

lines that contain a `# noqa` comment at the end will not issue warnings.

## installing ```Flake8```

```
$ pip install flake8
$ pip install --upgrade flake8
$ pip uninstall flake8
```

**You might want to use `sudo` to gain access to root**
