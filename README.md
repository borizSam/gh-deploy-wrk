# GitHub Actions Deployment Workflow

Este repositorio contiene un flujo de trabajo de **GitHub Actions** que despliega automáticamente los cambios realizados en el archivo `index.html` a **GitHub Pages**.

## 📌 Características
- Despliega automáticamente el sitio cuando se actualiza `index.html` en la rama `master`.
- Utiliza **GitHub Actions** para automatizar el proceso.
- Configura y publica la página en **GitHub Pages**.

## 🚀 Configuración y Uso

### 1️⃣ Clonar el repositorio
```bash
git https://github.com/borizSam/gh-deploy-wrk.git
cd gh-deploy-wrk
```

### 2️⃣ Crear y modificar `index.html`
Modifica el archivo `index.html` para personalizar el contenido del sitio.

### 3️⃣ Habilitar GitHub Pages
1. Ve a **Settings** → **Pages** en el repositorio.
2. En **Branch**, selecciona `master` y la carpeta `/ (root)`.
3. Guarda los cambios.

### 4️⃣ Workflow de GitHub Actions
El workflow se encuentra en `.github/workflows/deploy.yml` y contiene:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    paths:
      - "index.html"
    branches:
      - master

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Setup Pages
        uses: actions/configure-pages@v3

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: .

      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v2
```

Este workflow:
1. Se activa solo si `index.html` cambia en la rama `main`.
2. Configura GitHub Pages.
3. Sube el contenido y despliega la web.

### 5️⃣ Hacer cambios y desplegar
Cada vez que edites `index.html`, ejecuta:
```bash
git add index.html
git commit -m "Actualización del sitio"
git push origin main
```
Esto activará el workflow y actualizará la página en **GitHub Pages**.

## 🌐 Ver el sitio desplegado
Tu sitio estará disponible en:
```
https://<tu-usuario>.github.io/gh-deployment-workflow/
```
```
[Tu sitio se deberia tener una ruta parecida a esta:] (https://borizsam.github.io/gh-deploy-wrk/)

[https://borizsam.github.io/gh-deploy-wrk/](https://borizsam.github.io/gh-deploy-wrk/)
```
---
✍️ Creado con **GitHub Actions** 🚀

