# 🚀 Simulador de Movimiento Parabólico con Rozamiento del Aire

[![HTML5 Canvas](https://img.shields.io/badge/HTML5-Canvas-orange.svg)](https://developer.mozilla.org/es/docs/Web/API/Canvas_API)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow.svg)](https://developer.mozilla.org/es/docs/Web/JavaScript)
[![CSS3](https://img.shields.io/badge/CSS3-Responsive-blue.svg)](https://developer.mozilla.org/es/docs/Web/CSS)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![GitHub Pages](https://img.shields.io/badge/Demo-GitHub%20Pages-brightgreen.svg)](https://luisfelipe25.github.io/Simulador_Movimiento_Parabolico/)

Simulador físico interactivo en tiempo real diseñado para modelar la trayectoria cinemática de un proyectil en dos dimensiones (X, Y). A diferencia del modelo idealizado en el vacío, este simulador integra **resistencia aerodinámica (coeficiente de rozamiento con el aire \\$)**, **altura inicial de lanzamiento (\\$)**, cálculo numérico/analítico ajustado del tiempo de vuelo (\\$), alcance máximo y altura máxima.

---

## 📐 Complejidad Matemática y Modelo Físico

En la física clásica simplificada (sin resistencia del aire), la trayectoria de un proyectil sigue una parábola simétrica exacta. Sin embargo, en entornos reales la fuerza de fricción viscosa o resistencia aerodinámica actúa en sentido opuesto al vector velocidad.

Este proyecto modela la trayectoria considerando un **coeficiente de rozamiento \\$**, lo cual modifica las ecuaciones diferenciales de movimiento e introduce un amortiguamiento en las componentes horizontal y vertical.

### Ecuaciones Paramétricas de Posición

La posición del proyectil en función del tiempo \\$ viene dada por:

#### Componente Horizontal \(t)\$
x(t) = v_0 \cos(\theta) \, t - \frac{1}{2} k \, v_0 \cos(\theta) \, t^2

#### Componente Vertical \(t)\$
y(t) = y_0 + v_0 \sin(\theta) \, t - \frac{1}{2} g \, t^2 - \frac{1}{2} k \, v_0 \sin(\theta) \, t^2

donde:
- **\\$**: Velocidad inicial de lanzamiento (\/s\$).
- **\$\theta\$**: Ángulo de tiro con respecto a la horizontal (\^\circ\).
- **\\$**: Aceleración de la gravedad (\$\\approx 9.81 \, m/s^2\$).
- **\\$**: Coeficiente de rozamiento / resistencia del aire.
- **\\$**: Altura inicial desde la que se efectúa el disparo (\\$).

---

### Tiempo de Vuelo Analítico (\\$)

El tiempo total de vuelo \\$ hasta la colisión con el suelo (\(T) = 0\$) se deduce resolviendo la condición límite cinemática con resistencia:

T = \left( \frac{v_0 \sin\theta}{g + k v_0 \sin\theta} \right) \left( 1 + \sqrt{1 + \frac{2 y_0 (g + k v_0 \sin\theta)}{v_0^2 \sin^2\theta}} \right)

---

## ✨ Características Principales

- **Simulación Gráfica en Tiempo Real**: Visualización dinámica de la curva de disparo y renderizado animación fotograma a fotograma (equestAnimationFrame).
- **Parámetros Físicos Configurables**:
  - Velocidad Inicial (\\$)
  - Ángulo de Disparo (\$\theta\$)
  - Aceleración de Gravedad (\\$)
  - Coeficiente de Rozamiento (\\$)
  - Altura Inicial (\\$)
- **Cálculos Automáticos de Métricas**:
  - Tiempo total de vuelo (\\$)
  - Alcance horizontal máximo (\\$)
  - Altura máxima alcanzada (\\$)
- **Diseño Responsive & UI Moderna**: Menú interactivo con fondo en video en alta definición, soporte *Mobile-First* y canvas dinámico auto-ajustable al tamaño de pantalla.

---

## 🛠️ Arquitectura del Sistema

`mermaid
graph TD
    A[Inicio / Menú con Video de Fondo] -->|Clic en Empezar| B[Interfaz del Simulador]
    B --> C[Panel de Parámetros Físicos: v0, θ, g, k, y0]
    C -->|Simular / Cambio de Parámetros| D[Motor de Cálculo Físico: calcularT, x_t, y_t]
    D --> E{Validación de Parámetros}
    E -->|Error: Seno=0 o Raíz Negativa| F[Notificación de Error en UI]
    E -->|Válido| G[Mapeo de Coordenadas en Canvas HTML5]
    G --> H[Renderizado de Trayectoria y Animación de Proyectil]
    H --> I[Métricas de Resultados: Tiempo, Alcance, Altura Máxima]
`

---

## 📁 Estructura del Repositorio

`	ext
Simulador_Movimiento_Parabolico/
├── index.html        # Aplicación web completa (HTML, CSS responsive, JavaScript & Canvas)
└── Fondo.mp4         # Video de fondo para el menú principal
`

---

## 🚀 Despliegue y Ejecución Local

No requiere ningún proceso de compilación ni servidores backend.

### 1. Clonar el repositorio
`ash
git clone https://github.com/LuisFelipe25/Simulador_Movimiento_Parabolico.git
cd Simulador_Movimiento_Parabolico
`

### 2. Abrir en el navegador
Simplemente abre el archivo index.html en tu navegador web preferido:
`ash
# En Windows (PowerShell)
Start-Process index.html
`

---

## 🌐 Demo En Vivo

Accede a la simulación interactiva desplegada en GitHub Pages:
👉 **[https://luisfelipe25.github.io/Simulador_Movimiento_Parabolico/](https://luisfelipe25.github.io/Simulador_Movimiento_Parabolico/)**

---

## 📜 Licencia

Este proyecto está bajo la Licencia [MIT](LICENSE). Libre para uso educativo, académico y personal.