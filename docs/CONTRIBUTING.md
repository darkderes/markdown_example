# Guía de Contribución

¡Gracias por tu interés en contribuir a este proyecto! Esta guía te ayudará a contribuir de manera efectiva.

## 🚀 Cómo Contribuir

### Reportar Bugs

Si encuentras un error, por favor:

1. **Verifica** que el bug no haya sido reportado anteriormente
2. **Crea un issue** usando la plantilla de bug report
3. **Incluye información detallada**:
   - Descripción clara del problema
   - Pasos para reproducir
   - Comportamiento esperado vs actual
   - Screenshots si aplica
   - Información del entorno

### Sugerir Mejoras

Para sugerir nuevas características:

1. **Revisa** los issues existentes para evitar duplicados
2. **Crea un issue** con la etiqueta "enhancement"
3. **Describe detalladamente**:
   - El problema que resuelve
   - La solución propuesta
   - Alternativas consideradas
   - Impacto en usuarios existentes

### Contribuir con Código

1. **Fork** el repositorio
2. **Crea una rama** para tu característica:
   ```bash
   git checkout -b feature/nombre-caracteristica
   ```
3. **Realiza tus cambios** siguiendo las guías de estilo
4. **Añade pruebas** si es aplicable
5. **Commit** tus cambios:
   ```bash
   git commit -m "feat: add nueva característica"
   ```
6. **Push** a tu fork:
   ```bash
   git push origin feature/nombre-caracteristica
   ```
7. **Crea un Pull Request**

## 📝 Estándares de Documentación

### Formato de Markdown

- Usa encabezados jerárquicos (`#`, `##`, `###`)
- Incluye tabla de contenidos para documentos largos
- Usa bloques de código con sintaxis específica
- Añade emojis para mejorar la legibilidad (opcional)
- Mantén líneas de máximo 100 caracteres

### Estructura de Archivos

```
docs/
├── README.md           # Introducción y índice
├── guia-basica.md     # Conceptos fundamentales
├── guia-avanzada.md   # Técnicas avanzadas
├── herramientas.md    # Herramientas recomendadas
└── ejemplos/          # Ejemplos prácticos
```

### Convenciones de Nomenclatura

- Archivos: `kebab-case.md`
- Encabezados: Title Case
- Códigos: `camelCase` o `snake_case` según el lenguaje

## 🧪 Proceso de Revisión

### Checklist para Pull Requests

- [ ] El código sigue las guías de estilo
- [ ] Se han añadido pruebas para nuevas características
- [ ] La documentación está actualizada
- [ ] Los commits siguen el formato conventional
- [ ] No hay conflictos de merge

### Criterios de Aceptación

- Código limpio y bien documentado
- Pruebas que cubran los casos principales
- Documentación clara y actualizada
- Compatibilidad con versiones existentes

## 📋 Plantillas

### Issue de Bug

```markdown
**Descripción del Bug**
Descripción clara y concisa del bug.

**Para Reproducir**
Pasos para reproducir el comportamiento:

1. Ve a '...'
2. Haz clic en '....'
3. Desplázate hacia '....'
4. Ver error

**Comportamiento Esperado**
Descripción clara de lo que esperabas que ocurriera.

**Screenshots**
Si aplica, añade screenshots para explicar el problema.

**Información Adicional**

- OS: [ej. macOS, Windows, Linux]
- Navegador: [ej. Chrome, Safari]
- Versión: [ej. 22]
```

### Pull Request

```markdown
**Descripción**
Breve descripción de los cambios realizados.

**Tipo de Cambio**

- [ ] Bug fix (no rompe funcionalidad existente)
- [ ] Nueva característica (no rompe funcionalidad existente)
- [ ] Breaking change (cambio que causa que funcionalidad existente no funcione)
- [ ] Actualización de documentación

**¿Cómo se ha probado?**
Describe las pruebas que realizaste para verificar tus cambios.

**Checklist:**

- [ ] Mi código sigue las guías de estilo
- [ ] He realizado una auto-revisión de mi código
- [ ] He comentado mi código en áreas difíciles de entender
- [ ] He actualizado la documentación correspondiente
- [ ] Mis cambios no generan nuevas advertencias
- [ ] He añadido pruebas que demuestran que mi corrección es efectiva
```

## 🏷️ Etiquetas

### Para Issues

- `bug` - Algo no funciona
- `enhancement` - Nueva característica o solicitud
- `documentation` - Mejoras o adiciones a documentación
- `good first issue` - Bueno para nuevos contribuidores
- `help wanted` - Se necesita ayuda extra
- `question` - Información adicional solicitada

### Para Pull Requests

- `ready for review` - Listo para revisión
- `work in progress` - Trabajo en progreso
- `needs changes` - Necesita cambios antes de merge

## 🤝 Código de Conducta

Este proyecto adhiere al Contributor Covenant Code of Conduct. Al participar, se espera que mantengas este código.

### Nuestro Compromiso

- Crear un ambiente acogedor e inclusivo
- Respetar diferentes puntos de vista y experiencias
- Aceptar críticas constructivas
- Enfocarse en lo que es mejor para la comunidad

### Comportamiento Esperado

- Usar lenguaje acogedor e inclusivo
- Respetar diferentes puntos de vista
- Aceptar críticas constructivas
- Mostrar empatía hacia otros miembros

## 📞 Contacto

Si tienes preguntas sobre la contribución:

- Crea un issue con la etiqueta "question"
- Contacta a los mantenedores
- Únete a nuestras discusiones

---

¡Gracias por contribuir! 🎉
