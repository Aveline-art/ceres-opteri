# ceres-opteri

[Ceres Opteri](https://aveline-art.github.io/ceres-opteri/) (or anagram for Recipe Store) is a static website for recipes.

## Instructions

1. Create a venv and activate it. I usually use VSCode so it is automatically activated.

```
python -m venv .venv
source .venv/bin/activate
```

2. Install dependencies.

```
pip install pelican
pip install ghp-import
```

3. (Optional) Install a theme. If you do, specify the path where the theme is installed in pelicanconf.py. I use [eevee](https://github.com/kura/eevee).

```
# I installed the theme as a sibling in the project folder.
THEME = "../eevee"
```

4. Start the local development server.

```
pelican -r -l
```

5. (Optional) Preview the static website before deployment.

```
pelican content -o output -s publishconf.py
```

6. Run make to deploy to github pages.

```
make github
```

## Troubleshooting

1. Help! Somehow the website does not look the same when I am developing locally vs when deployed.

This is probably because of a mixup of settings. Here is roughly how Pelican works. When developing locally, it uses the settings in `pelicanconf.py`. However, when deployed to production, it uses the settings in `pelicanconf.py` **and** `publishconf.py`. This means that any settings in `publishconf.py` will override `pelicanconf.py` if the setting variables coincide. This is useful, for example, when setting paths to links locally vs in production. However, if the settings are carelessly changed, it can cause confusing bugs to happen.
