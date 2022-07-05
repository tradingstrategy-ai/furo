Fork of [Furo Sphinx theme](https://pradyunsg.me/furo/) with different colours.

- Added as a git submodule to [docs](https://github.com/tradingstrategy-ai/docs)
- Added as an development Poetry dependency

Building theme
==============

To rebuild CSS files:

```shell
npm install
npm run build
```

This will generate`theme/furo/static/styles/furo.css`

Now update the CSS file in the main docs repository
and place it to our Sphinx installation `_static/styles` folder:

```shell
cp deps/furo/src/furo/theme/furo/static/styles/furo.css source/_static/styles
```

Because of Sphinx template/static override resolution,
your custom build `furo.css` will be picked over the default one.

Updating theme
==============

Edit Furo SASS files directy to change colour variables.

[Edit _colors.sass](./src/furo/assets/styles/variables/_colors.scss).

`colors-dark` depends on `colors` being included at a lower specificity.

Preview
=======

Just rebuild theme and then rebuild docs with:

```shell
make clean html
```

Updating from upstream
======================

git pull changes from Furo master.

Troubleshooting
===============

Poetry does not recognise Furo filesystem checkout as a Python package and the following
fails:

```
furo = {path = "deps/trade-executor", develop = true}
```

Thus, the CSS copy hack