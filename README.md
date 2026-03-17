# Suto Studio — Demos para leads

Prototipos de BackOffice personalizados para leads de Suto Studio.  
Cada subcarpeta dentro de `demos/` es un prototipo independiente que se publica automáticamente.

## Estructura

```
demos/
├── hibelecars/
│   └── index.html
├── otra-empresa/
│   └── index.html
└── index.html
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
```

## Notas

- Los prototipos tienen `<meta name="robots" content="noindex, nofollow">` para que Google no los indexe
- Cada HTML es autónomo (no depende de archivos locales, solo CDNs de Google Fonts y Chart.js)
- El repo es público pero las URLs no son descubribles sin el enlace directo
