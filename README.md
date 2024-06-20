# docs.ichipro.sasakulab.com

The documentation for the Ichipro Project.

## Set Up

```zsh
git clone https://github.com/ichipro-hcu/docs.ichipro.sasakulab.com.git // Git
# gh repo clone ichipro-hcu/docs.ichipro.sasakulab.com // GitHub CLI
cd docs.ichipro.sasakulab.com
rye sync
```

## Commands

### Serve the Document for Writing

```zsh
mkdocs serve # Start the live-reloading docs server.
```

### Deploying the Document

If you commited and pushed the changes to the repository, the document will be automatically deployed to the GitHub Pages when the change was merged to `master`.
