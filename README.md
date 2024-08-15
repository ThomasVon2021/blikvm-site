# BLIKVM website

[![Discord](https://img.shields.io/discord/943534043515977768?color=0&label=chat&logo=discord)](https://discord.gg/9Y374gUF6C)

This repo is the <a href="https://wiki.blicube.com/blikvm/en/" target="_blank">BLIKVM website</a> manual. The manual has Multilingual support. We highly encourage you to translate your own language for the BliKVM user manual. If you are interested in becoming a translation contributor,
you can submit a PR. We will thank you very much for your translation work.

## File Structure

You can add your language by following this structure.

```bash
├─ config/
│    ├─ en/
│    │  └─ mkdocs.yml
│    ├─ zh/
│    │  └─ mkdocs.yml
│    └─ xxx/
│        └─ mkdocs.yml
│
├─ generated/
│    ├─ en/
│    ├─ zh/
│    └─ xxx/
│
├─ docs/
│    ├─ en/
│    │   ├─ index.md 
│    │   └─ xxx.md
│    ├─ zh/
│    │   ├─ index.md 
│    │   └─ xxx.md
│    └─ xx/
│        ├─ index.md 
│        └─ xxx.md
│
└─ overrides/
     └─assets/
        └─images/
```

## Establishment of development environment

If you don't know about mkdocs, please study from <a href="https://squidfunk.github.io/mkdocs-material/getting-started/" target="_blank">mkdocs website</a>. When you follow the website and set up the use environment of mkdocs, you can run the project with the following command to preview:

```bash
mkdocs serve -f config/en/mkdocs.yml
```

You can change language path, if you modify chinese part, the command like this:

```bash
mkdocs serve -f config/zh/mkdocs.yml
```

If there is no problem with the environment installation, you will see an output similar to the following. You can preview the website by inputting the IP address (eg:http://127.0.0.1:8000/) to the browser.

```bash
(venv) shangbinbin@shangbibindeMBP blikvm-site % mkdocs serve -f config/en/mkdocs.yml
INFO     -  Building documentation...
INFO     -  Cleaning site directory
INFO     -  Documentation built in 1.08 seconds
INFO     -  [16:56:09] Watching paths for changes: 'docs/en', 'config/en/mkdocs.yml'
INFO     -  [16:56:09] Serving on http://127.0.0.1:8000/
INFO     -  [16:56:12] Browser connected: http://127.0.0.1:8000/update/
```

When the preview results are confirmed to be correct, you can use the following command to complete the compilation and packaging. Then you can merge your commit by PR.

```bash
bash build.sh
```

## Acknowledgments

<a href="https://www.mkdocs.org/" target="_blank">mkdocs</a>
<a href="https://github.com/nishiku" target="_blank">Masao NISHIKU</a>
<a href="https://github.com/GordoNice" target="_blank">Ivan Gordeev</a>
