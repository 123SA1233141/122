<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Мой первый сайт</title>
</head>
<body>
    <h1>Добро пожаловать на мой сайт!</h1>
    <p>Это мой первый сайт, созданный с нуля.</p>
 jobs:
  # Single deploy job no building
  deploy:
    environment:
      name: github-pages
      url: ${{steps.deployment.outputs.page_url}}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Pages
        uses: actions/configure-pages@v5
      - name: Upload Artifact
        uses: actions/upload-pages-artifact@v3
        with:
          # upload entire directory
          path: '.'
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4  
