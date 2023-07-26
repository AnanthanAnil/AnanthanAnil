<h2 align="center">Hi 👋! My name is Ananthan.A</h2>

###

<div align="left">
</div>

###

<h4 align="left">Dedicated Mechanical Engineer with the experience and technical<br>expertise to provide the highest quality mechanical component and<br>system support. Skilled at formulating and implementing<br>equipment designs, testing and producing specifications, and<br>researching product application.</h4>

###

<div align="left">
  <img src="https://skillicons.dev/icons?i=pr" height="30" alt="adobepremierepro logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=ps" height="30" alt="adobephotoshop logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=ai" height="30" alt="adobeillustrator logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=autocad" height="30" alt="autocad logo"  />
</div>

###

<img align="left" height="150" src="https://media1.giphy.com/media/yTwTUGfiaKL3fgZWLN/giphy.gif"  />

###

<div align="left">
  <img src="https://img.shields.io/static/v1?message=Gmail&logo=gmail&label=&color=D14836&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="gmail logo"  />
  <img src="https://img.shields.io/static/v1?message=LinkedIn&logo=linkedin&label=&color=0077B5&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="linkedin logo"  />
  <img src="https://img.shields.io/static/v1?message=Behance&logo=behance&label=&color=1769ff&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="behance logo"  />
</div>

###

<br clear="both">

<img src="https://raw.githubusercontent.com/AnanthanAnil/AnanthanAnil/output/snake.svg" alt="Snake animation" />

###
name: Generate snake animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - master

jobs:
  generate:
    runs-on: ubuntu-latest

    steps:
      - name: generate snake.svg
        uses: Platane/snk/svg-only@v2
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: dist/snake.svg


      - name: push snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v2.6.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
