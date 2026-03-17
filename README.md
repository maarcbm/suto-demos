# Suto Studio — Demos para leads

Prototipos de BackOffice personalizados para leads de Suto Studio.  
Cada subcarpeta dentro de `demos/` es un prototipo independiente que se publica automáticamente.

## Estructura

```
demos/
├── hibelecars/
│   └── index.html      ← demo.sutostudio.com/hibelecars
├── otra-empresa/
│   └── index.html      ← demo.sutostudio.com/otra-empresa
└── index.html           ← landing page (opcional)
```

## Cómo funciona

1. **Generas un prototipo** en Claude con el skill `lead-prototype-generator`
2. **Descargas el HTML** y lo colocas en `demos/{nombre-empresa}/index.html`
3. **Push a `main`** → GitHub Actions despliega automáticamente a GitHub Pages
4. **Envías el link** al lead: `https://demo.sutostudio.com/{nombre-empresa}`

## Setup inicial (una sola vez)

### 1. Crear el repo en GitHub
```bash
gh repo create suto-demos --private --source=. --push
```

### 2. Activar GitHub Pages
- Ve a **Settings → Pages**
- Source: **GitHub Actions**

### 3. Configurar dominio personalizado
- En **Settings → Pages → Custom domain**, pon: `demo.sutostudio.com`
- En tu proveedor DNS, crea un registro CNAME:
  ```
  demo.sutostudio.com → tu-usuario.github.io
  ```
- Marca "Enforce HTTPS"

### 4. Primer deploy
```bash
git add .
git commit -m "feat: primer prototipo - hibelecars"
git push origin main
```

## Flujo rápido para nuevos leads

```bash
# 1. Descarga el HTML de Claude
# 2. Crea la carpeta y copia el archivo
mkdir -p demos/nombre-empresa
cp ~/Downloads/nombre-empresa-backoffice.html demos/nombre-empresa/index.html

# 3. Push
git add demos/nombre-empresa
git commit -m "feat: prototipo para nombre-empresa"
git push

# 4. En ~1 minuto estará en: https://demo.sutostudio.com/nombre-empresa
```

## Notas

- Los prototipos tienen `<meta name="robots" content="noindex, nofollow">` para que Google no los indexe
- Cada HTML es autónomo (no depende de archivos locales, solo CDNs de Google Fonts y Chart.js)
- El repo puede ser privado — GitHub Pages funciona con repos privados en planes Pro/Team
