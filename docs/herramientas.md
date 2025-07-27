# Herramientas para Markdown

## Editores de Markdown

### Visual Studio Code
**Extensiones recomendadas:**
- Markdown All in One
- Markdown Preview Enhanced
- markdownlint
- Markdown PDF
- Paste Image

**Configuración sugerida:**
```json
{
  "markdown.preview.fontSize": 14,
  "markdown.preview.lineHeight": 1.6,
  "markdown.extension.toc.levels": "1..6",
  "markdown.extension.orderedList.marker": "one"
}
```

### Typora
- Editor WYSIWYG
- Vista previa en tiempo real
- Soporte para matemáticas y diagramas
- Temas personalizables

### Mark Text
- Editor gratuito y de código abierto
- Vista previa en tiempo real
- Soporte para Mermaid y matemáticas
- Modo enfoque y máquina de escribir

## Linters y Formateadores

### markdownlint

Instalar:
```bash
npm install -g markdownlint-cli
```

Uso:
```bash
markdownlint *.md
markdownlint docs/
```

Configuración (`.markdownlint.json`):
```json
{
  "MD013": {
    "line_length": 100
  },
  "MD033": false,
  "MD041": false
}
```

### Prettier

Configuración para Markdown:
```json
{
  "printWidth": 80,
  "proseWrap": "always",
  "overrides": [
    {
      "files": "*.md",
      "options": {
        "printWidth": 100,
        "proseWrap": "preserve"
      }
    }
  ]
}
```

## Generadores de Sitios

### GitBook
```bash
npm install -g gitbook-cli
gitbook init
gitbook serve
```

### Docsify
```bash
npm install -g docsify-cli
docsify init ./docs
docsify serve docs
```

### VuePress
```bash
npm install -g vuepress
mkdir docs && echo '# Hello VuePress' > docs/README.md
vuepress dev docs
```

## Conversores de Formato

### Pandoc
Convertir Markdown a otros formatos:

```bash
# Markdown a PDF
pandoc documento.md -o documento.pdf

# Markdown a Word
pandoc documento.md -o documento.docx

# Markdown a HTML
pandoc documento.md -o documento.html
```

### markdown-pdf (Node.js)
```bash
npm install -g markdown-pdf
markdown-pdf documento.md
```

## Herramientas Online

### Editores Online
- **Dillinger**: Editor online con vista previa
- **StackEdit**: Editor con sincronización en la nube
- **Markdown Editor**: Simple y rápido
- **HackMD**: Colaborativo en tiempo real

### Generadores de Tablas
- **Tables Generator**: Crea tablas Markdown visualmente
- **Markdown Table Generator**: Generador simple de tablas

### Diagramas
- **Mermaid Live Editor**: Editor online para diagramas Mermaid
- **Draw.io**: Diagramas que se pueden exportar como SVG

## Integración con Git

### Pre-commit hooks

`.pre-commit-config.yaml`:
```yaml
repos:
  - repo: https://github.com/igorshubovych/markdownlint-cli
    rev: v0.31.1
    hooks:
      - id: markdownlint
        args: ['--fix']
```

### GitHub Actions

`.github/workflows/markdown-lint.yml`:
```yaml
name: Markdown Lint

on: [push, pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Lint Markdown files
        uses: avto-dev/markdown-lint@v1
        with:
          args: '**/*.md'
```

## Mejores Prácticas para Herramientas

### 1. Configuración de Proyecto

Crear `.editorconfig`:
```ini
root = true

[*.md]
charset = utf-8
end_of_line = lf
insert_final_newline = true
trim_trailing_whitespace = true
indent_style = space
indent_size = 2
```

### 2. Scripts NPM útiles

`package.json`:
```json
{
  "scripts": {
    "docs:lint": "markdownlint docs/**/*.md",
    "docs:fix": "markdownlint --fix docs/**/*.md",
    "docs:serve": "docsify serve docs",
    "docs:build": "vuepress build docs"
  }
}
```

### 3. Plantillas de Issues y PRs

`.github/ISSUE_TEMPLATE/bug_report.md`:
```markdown
---
name: Bug report
about: Create a report to help us improve
title: ''
labels: ''
assignees: ''
---

**Describe the bug**
A clear and concise description of what the bug is.

**To Reproduce**
Steps to reproduce the behavior:
1. Go to '...'
2. Click on '....'
3. Scroll down to '....'
4. See error

**Expected behavior**
A clear and concise description of what you expected to happen.

**Screenshots**
If applicable, add screenshots to help explain your problem.

**Desktop (please complete the following information):**
 - OS: [e.g. iOS]
 - Browser [e.g. chrome, safari]
 - Version [e.g. 22]

**Additional context**
Add any other context about the problem here.
```

## Automatización

### Generar Tabla de Contenidos
```bash
# Con markdown-toc
npm install -g markdown-toc
markdown-toc -i README.md
```

### Validación Automática
```bash
# Script de validación
#!/bin/bash
echo "Verificando sintaxis Markdown..."
markdownlint docs/**/*.md

echo "Verificando enlaces rotos..."
markdown-link-check docs/**/*.md

echo "Generando tabla de contenidos..."
markdown-toc -i README.md
```

---

📚 Anterior: [Guía Avanzada](guia-avanzada.md)
