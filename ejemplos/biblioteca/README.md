# MathUtils - Biblioteca de Utilidades Matemáticas

[![npm version](https://badge.fury.io/js/mathutils-lib.svg)](https://badge.fury.io/js/mathutils-lib)
[![Build Status](https://travis-ci.org/usuario/mathutils.svg?branch=main)](https://travis-ci.org/usuario/mathutils)
[![Coverage Status](https://coveralls.io/repos/github/usuario/mathutils/badge.svg?branch=main)](https://coveralls.io/github/usuario/mathutils?branch=main)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Una biblioteca JavaScript ligera y eficiente que proporciona funciones matemáticas comunes para aplicaciones web y Node.js.

## ✨ Características

- 🚀 **Rendimiento optimizado** - Algoritmos eficientes y optimizados
- 📦 **Ligera** - Sin dependencias externas
- 🔧 **TypeScript** - Soporte completo para TypeScript
- 🧪 **Bien probada** - Cobertura de pruebas del 100%
- 📚 **Bien documentada** - Documentación completa con ejemplos
- 🌍 **Universal** - Funciona en navegadores y Node.js

## 📋 Tabla de Contenidos

- [Instalación](#instalación)
- [Uso Básico](#uso-básico)
- [API Reference](#api-reference)
- [Ejemplos](#ejemplos)
- [Desarrollo](#desarrollo)
- [Contribuir](#contribuir)
- [Licencia](#licencia)

## 🚀 Instalación

### npm

```bash
npm install mathutils-lib
```

### yarn

```bash
yarn add mathutils-lib
```

### CDN

```html
<script src="https://unpkg.com/mathutils-lib@latest/dist/mathutils.min.js"></script>
```

## 💻 Uso Básico

### ES6 Modules

```javascript
import MathUtils from "mathutils-lib";

// Calcular factorial
const factorial = MathUtils.factorial(5); // 120

// Verificar si es primo
const isPrime = MathUtils.isPrime(17); // true

// Calcular fibonacci
const fib = MathUtils.fibonacci(10); // 55
```

### CommonJS

```javascript
const MathUtils = require("mathutils-lib");

console.log(MathUtils.gcd(48, 18)); // 6
console.log(MathUtils.lcm(4, 6)); // 12
```

### Navegador

```html
<script src="https://unpkg.com/mathutils-lib@latest/dist/mathutils.min.js"></script>
<script>
  console.log(MathUtils.isPerfect(28)); // true
</script>
```

## 📖 API Reference

### Funciones Básicas

#### `factorial(n: number): number`

Calcula el factorial de un número.

**Parámetros:**

- `n` - Número entero no negativo

**Retorna:** El factorial de n

**Ejemplo:**

```javascript
MathUtils.factorial(5); // 120
MathUtils.factorial(0); // 1
```

**Complejidad:** O(n)

---

#### `fibonacci(n: number): number`

Calcula el n-ésimo número de Fibonacci.

**Parámetros:**

- `n` - Posición en la secuencia (≥ 0)

**Retorna:** El n-ésimo número de Fibonacci

**Ejemplo:**

```javascript
MathUtils.fibonacci(0); // 0
MathUtils.fibonacci(1); // 1
MathUtils.fibonacci(10); // 55
```

**Complejidad:** O(n)

---

#### `isPrime(n: number): boolean`

Determina si un número es primo.

**Parámetros:**

- `n` - Número entero a verificar

**Retorna:** `true` si es primo, `false` en caso contrario

**Ejemplo:**

```javascript
MathUtils.isPrime(2); // true
MathUtils.isPrime(17); // true
MathUtils.isPrime(4); // false
```

**Complejidad:** O(√n)

### Funciones de Teoría de Números

#### `gcd(a: number, b: number): number`

Calcula el Máximo Común Divisor usando el algoritmo de Euclides.

**Parámetros:**

- `a` - Primer número
- `b` - Segundo número

**Retorna:** El MCD de a y b

**Ejemplo:**

```javascript
MathUtils.gcd(48, 18); // 6
MathUtils.gcd(17, 13); // 1
```

---

#### `lcm(a: number, b: number): number`

Calcula el Mínimo Común Múltiplo.

**Parámetros:**

- `a` - Primer número
- `b` - Segundo número

**Retorna:** El MCM de a y b

**Ejemplo:**

```javascript
MathUtils.lcm(4, 6); // 12
MathUtils.lcm(15, 20); // 60
```

---

#### `isPerfect(n: number): boolean`

Determina si un número es perfecto (igual a la suma de sus divisores propios).

**Parámetros:**

- `n` - Número a verificar

**Retorna:** `true` si es perfecto, `false` en caso contrario

**Ejemplo:**

```javascript
MathUtils.isPerfect(6); // true (1 + 2 + 3 = 6)
MathUtils.isPerfect(28); // true (1 + 2 + 4 + 7 + 14 = 28)
MathUtils.isPerfect(12); // false
```

### Funciones Estadísticas

#### `mean(numbers: number[]): number`

Calcula la media aritmética.

**Parámetros:**

- `numbers` - Array de números

**Retorna:** La media aritmética

**Ejemplo:**

```javascript
MathUtils.mean([1, 2, 3, 4, 5]); // 3
MathUtils.mean([10, 20, 30]); // 20
```

---

#### `median(numbers: number[]): number`

Calcula la mediana.

**Parámetros:**

- `numbers` - Array de números

**Retorna:** La mediana

**Ejemplo:**

```javascript
MathUtils.median([1, 2, 3, 4, 5]); // 3
MathUtils.median([1, 2, 3, 4]); // 2.5
```

---

#### `mode(numbers: number[]): number[]`

Encuentra el/los valor(es) que aparecen más frecuentemente.

**Parámetros:**

- `numbers` - Array de números

**Retorna:** Array con los valores modales

**Ejemplo:**

```javascript
MathUtils.mode([1, 2, 2, 3, 4]); // [2]
MathUtils.mode([1, 1, 2, 2, 3]); // [1, 2]
```

---

#### `standardDeviation(numbers: number[]): number`

Calcula la desviación estándar.

**Parámetros:**

- `numbers` - Array de números

**Retorna:** La desviación estándar

**Ejemplo:**

```javascript
MathUtils.standardDeviation([1, 2, 3, 4, 5]); // ~1.58
```

### Funciones de Geometría

#### `distance(point1: Point, point2: Point): number`

Calcula la distancia euclidiana entre dos puntos.

**Parámetros:**

- `point1` - Primer punto `{x: number, y: number}`
- `point2` - Segundo punto `{x: number, y: number}`

**Retorna:** La distancia entre los puntos

**Ejemplo:**

```javascript
MathUtils.distance({ x: 0, y: 0 }, { x: 3, y: 4 }); // 5
```

---

#### `circleArea(radius: number): number`

Calcula el área de un círculo.

**Parámetros:**

- `radius` - Radio del círculo

**Retorna:** El área del círculo

**Ejemplo:**

```javascript
MathUtils.circleArea(5); // ~78.54
```

## 🔧 Desarrollo

### Configuración del Entorno

```bash
# Clonar el repositorio
git clone https://github.com/usuario/mathutils.git
cd mathutils

# Instalar dependencias
npm install

# Ejecutar en modo desarrollo
npm run dev
```

### Scripts Disponibles

```bash
# Desarrollo
npm run dev          # Modo desarrollo con watch
npm run build        # Compilar para producción
npm run build:types  # Generar archivos de definición TypeScript

# Testing
npm test            # Ejecutar todas las pruebas
npm run test:watch  # Ejecutar pruebas en modo watch
npm run test:coverage # Generar reporte de cobertura

# Linting y Formateo
npm run lint        # Verificar código con ESLint
npm run lint:fix    # Corregir problemas de linting automáticamente
npm run format      # Formatear código con Prettier

# Documentación
npm run docs        # Generar documentación
npm run docs:serve  # Servir documentación localmente
```

### Estructura del Proyecto

```
mathutils/
├── src/                    # Código fuente
│   ├── index.ts           # Punto de entrada principal
│   ├── basic.ts           # Funciones básicas
│   ├── statistics.ts      # Funciones estadísticas
│   ├── geometry.ts        # Funciones geométricas
│   └── types.ts           # Definiciones de tipos
├── tests/                 # Pruebas
│   ├── basic.test.ts
│   ├── statistics.test.ts
│   └── geometry.test.ts
├── docs/                  # Documentación
├── dist/                  # Archivos compilados
├── examples/              # Ejemplos de uso
├── .github/               # Configuración de GitHub
│   └── workflows/         # GitHub Actions
├── package.json
├── tsconfig.json
├── jest.config.js
├── .eslintrc.js
└── README.md
```

### Ejecutar Pruebas

```bash
# Todas las pruebas
npm test

# Pruebas específicas
npm test -- --grep "factorial"

# Con coverage
npm run test:coverage
```

### Ejemplo de Prueba

```javascript
import MathUtils from "../src/index";

describe("Basic Math Functions", () => {
  describe("factorial", () => {
    it("should calculate factorial correctly", () => {
      expect(MathUtils.factorial(0)).toBe(1);
      expect(MathUtils.factorial(1)).toBe(1);
      expect(MathUtils.factorial(5)).toBe(120);
    });

    it("should throw error for negative numbers", () => {
      expect(() => MathUtils.factorial(-1)).toThrow();
    });
  });

  describe("fibonacci", () => {
    it("should calculate fibonacci numbers correctly", () => {
      expect(MathUtils.fibonacci(0)).toBe(0);
      expect(MathUtils.fibonacci(1)).toBe(1);
      expect(MathUtils.fibonacci(10)).toBe(55);
    });
  });
});
```

## 📊 Rendimiento

### Benchmarks

| Función          | Operaciones/seg | Complejidad |
| ---------------- | --------------- | ----------- |
| factorial(100)   | ~1,000,000      | O(n)        |
| fibonacci(40)    | ~100,000        | O(n)        |
| isPrime(1000000) | ~10,000         | O(√n)       |
| gcd(large_nums)  | ~5,000,000      | O(log n)    |

### Optimizaciones

- **Memoización**: Fibonacci usa caché para resultados previos
- **Algoritmos eficientes**: GCD usa algoritmo de Euclides
- **Validación temprana**: Verificaciones rápidas para casos especiales

## 🏗️ Arquitectura

### Principios de Diseño

1. **Modularidad**: Cada función es independiente y reutilizable
2. **Inmutabilidad**: Las funciones no modifican los parámetros de entrada
3. **Consistencia**: API consistente en toda la biblioteca
4. **Rendimiento**: Algoritmos optimizados para casos comunes

### Patrones Utilizados

- **Factory Pattern**: Para crear instancias configurables
- **Strategy Pattern**: Para diferentes algoritmos de la misma operación
- **Pure Functions**: Todas las funciones son puras (sin efectos secundarios)

## 🤝 Contribuir

¡Las contribuciones son bienvenidas! Ver [CONTRIBUTING.md](CONTRIBUTING.md) para detalles.

### Proceso de Contribución

1. **Fork** el repositorio
2. **Crea** una rama para tu característica (`git checkout -b feature/nueva-funcion`)
3. **Commit** tus cambios (`git commit -am 'Añadir nueva función matemática'`)
4. **Push** a la rama (`git push origin feature/nueva-funcion`)
5. **Crea** un Pull Request

### Estándares de Código

- Sigue las reglas de ESLint configuradas
- Añade pruebas para nuevas funciones
- Actualiza la documentación
- Usa TypeScript para todas las nuevas funciones

### Reportar Bugs

Usa la [plantilla de issues](https://github.com/usuario/mathutils/issues/new?template=bug_report.md) para reportar bugs.

## 📄 Licencia

Este proyecto está licenciado bajo la Licencia MIT. Ver [LICENSE](LICENSE) para detalles.

```
MIT License

Copyright (c) 2024 Tu Nombre

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

## 📞 Soporte

- 📧 **Email**: soporte@mathutils.com
- 🐛 **Issues**: [GitHub Issues](https://github.com/usuario/mathutils/issues)
- 💬 **Discusiones**: [GitHub Discussions](https://github.com/usuario/mathutils/discussions)
- 📚 **Wiki**: [GitHub Wiki](https://github.com/usuario/mathutils/wiki)

## 🙏 Agradecimientos

- Gracias a todos los [contribuidores](CONTRIBUTORS.md)
- Inspirado por bibliotecas como Lodash y NumPy
- Documentación basada en las mejores prácticas de MDN

---

Hecho con ❤️ por [Tu Nombre](https://github.com/tu-usuario)
