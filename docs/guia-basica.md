# Guía Básica de Markdown

## ¿Qué es Markdown?

Markdown es un lenguaje de marcado ligero que permite dar formato a texto plano de manera sencilla y legible. Es ampliamente utilizado en desarrollo de software para:

- Documentación de proyectos (README.md)
- Wikis y documentación técnica
- Issues y pull requests en GitHub/GitLab
- Comentarios en código
- Blogs técnicos

## Sintaxis Básica

### Encabezados

```markdown
# Encabezado Nivel 1

## Encabezado Nivel 2

### Encabezado Nivel 3

#### Encabezado Nivel 4

##### Encabezado Nivel 5

###### Encabezado Nivel 6
```

### Énfasis

```markdown
_Texto en cursiva_ o _texto en cursiva_
**Texto en negrita** o **texto en negrita**
**_Texto en cursiva y negrita_**
~~Texto tachado~~
```

Resultado:

- _Texto en cursiva_
- **Texto en negrita**
- **_Texto en cursiva y negrita_**
- ~~Texto tachado~~

### Listas

#### Lista no ordenada

```markdown
- Elemento 1
- Elemento 2
  - Subelemento 2.1
  - Subelemento 2.2
- Elemento 3
```

#### Lista ordenada

```markdown
1. Primer elemento
2. Segundo elemento
   1. Subelemento 2.1
   2. Subelemento 2.2
3. Tercer elemento
```

### Enlaces

```markdown
[Texto del enlace](https://ejemplo.com)
[Enlace con título](https://ejemplo.com "Título del enlace")
[Enlace de referencia][1]

[1]: https://ejemplo.com
```

### Imágenes

```markdown
![Texto alternativo](ruta/a/imagen.png)
![Imagen con título](ruta/a/imagen.png "Título de la imagen")
```

### Código

#### Código en línea

```markdown
Use la función `console.log()` para depurar.
```

#### Bloques de código

````markdown
```javascript
function saludo(nombre) {
  console.log(`Hola, ${nombre}!`);
}
```
````

````

### Citas

```markdown
> Esta es una cita.
> Puede tener múltiples líneas.
>
> Y múltiples párrafos.
````

### Tablas

```markdown
| Columna 1 | Columna 2 | Columna 3 |
| --------- | --------- | --------- |
| Fila 1    | Dato 1    | Dato 2    |
| Fila 2    | Dato 3    | Dato 4    |
```

### Líneas Horizontales

```markdown
---
```

## Mejores Prácticas Básicas

1. **Usa encabezados de forma jerárquica**: Comienza con `#` y usa niveles consecutivos
2. **Deja líneas en blanco**: Entre secciones para mejorar la legibilidad
3. **Sé consistente**: Usa el mismo estilo para elementos similares
4. **Incluye tabla de contenidos**: Para documentos largos
5. **Usa listas**: Para organizar información de forma clara

---

📚 Siguiente: [Guía Avanzada](guia-avanzada.md)
