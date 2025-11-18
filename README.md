# 🎮 Lluvia de Letras – Evaluación 4 (Organización de Computadores)

**Lluvia de Letras** es un videojuego desarrollado completamente en **lenguaje Jack** sobre la plataforma **Nand2Tetris**, como entrega académica para la asignatura **Organización de Computadores**.  
El propósito del proyecto es demostrar dominio sobre el funcionamiento del lenguaje Jack, la estructura del Sistema Operativo del curso, el ciclo de ejecución, el uso del teclado, el renderizado en pantalla y el diseño modular orientado a objetos.

---

## 📌 Descripción General del Juego

Lluvia de Letras es un juego tipo arcade donde **letras y palabras completas caen desde la parte superior de la pantalla**.  
El jugador debe **teclearlas antes de que toquen el suelo**.

El juego incorpora:

- Letras individuales que caen verticalmente.
- Palabras completas que caen horizontalmente ocupando varias columnas contiguas.
- Un sistema de vidas (3 vidas).
- Sistema de puntuación.
- Sistema de combos (activado tras acertar 10 letras/palabras consecutivas).
- Renderizado totalmente gráfico utilizando `Screen` y `Output`.
- Reserva de columnas para palabras (no permite superposición).
- Pantalla de Game Over.
- HUD con puntaje, vidas y combo.

---

## 🕹️ Mecánicas Principales

### ✔ Letras individuales
- Se generan en columnas libres.
- Caen de forma continua hacia abajo.
- Si el jugador presiona la letra correspondiente → se elimina y suma puntos.

### ✔ Palabras completas (diferenciador del juego)
- Se generan horizontalmente.
- Para aparecer necesitan **columnas consecutivas libres**.
- Si una columna está ocupada por otra palabra, no puede generarse allí.
- Presionar una letra que pertenece a la palabra elimina **toda la palabra**.
- Otorga una bonificación mayor que las letras sueltas.

### ✔ Sistema de vidas
- El jugador inicia con **3 vidas**.
- Si una letra o palabra toca el suelo → se pierde una vida.
- Con 0 vidas → **Game Over**.

### ✔ Combos
- Se activa tras **10 aciertos consecutivos**.
- Aumenta progresivamente cada 5 aciertos adicionales.
- Incrementa la multiplicación de puntos.

### ✔ Renderizado gráfico
Se utilizan funciones del OS:
- `Screen.drawRectangle()` → dibuja bloques para cada letra/palabra.
- `Output.printChar()` → dibuja la letra encima del bloque.
- `Output.printInt()` y `Output.printString()` → HUD.

---

## 🧩 Arquitectura del Proyecto

El proyecto se divide en módulos, cumpliendo con un diseño limpio y evaluable según la rúbrica:

### **1. Game.jack**
- Control del ciclo principal del juego.
- Inicialización del sistema.
- Control del tiempo mediante `Sys.wait()`.
- Gestión de vidas, puntaje y combo.
- Renderizado del HUD.
- Pantalla de Game Over.

### **2. WordManager.jack**
- Manejo de letras individuales.
- Manejo de palabras completas.
- Cálculo de posiciones X e Y.
- Control de caída.
- Verificación de espacio para generar palabras.
- Reserva de columnas para evitar superposición.
- Detección de colisión con el suelo.
- Eliminación de elementos.
- Generación aleatoria de nuevas letras/palabras.

### **3. PlayerInput.jack**
- Lectura del teclado con `Keyboard.readChar()`.
- Validación de letras presionadas.
- Eliminación de letras/palabras acertadas.
- Reinicio y actualización de racha para combos.

### **4. ScoreSystem.jack**
- Cálculo de puntaje según:
  - Letras individuales.
  - Palabras completas.
- Activación de combos tras 10 aciertos.
- Multiplicador de combo.
- Actualización del HUD.

### **5. Renderer.jack**
- Renderizado gráfico de cada letra y palabra.
- HUD (vidas, puntaje, combo).
- Limpieza de pantalla.
- Renderizado de Game Over.

---

## 📁 Estructura del Proyecto

El repositorio debe tener la siguiente estructura:
```
Lluvia_de_letras_Evaluacion_4/
│── Game.jack
│── Renderer.jack
│── WordManager.jack
│── PlayerInput.jack
│── ScoreSystem.jack
│
└── OS/
    │── Sys.jack
    │── Screen.jack
    │── Keyboard.jack
    │── Output.jack
    │── Memory.jack
    │── Math.jack
    │── String.jack
```



> **Los archivos del OS son obligatorios para que el JackCompiler genere correctamente los .vm del juego.**

---

## 🛠️ Cómo Compilar (Jack → VM)

Puedes compilar el proyecto con cualquiera de estos dos métodos:

### ✔ Opción A — JackCompiler Desktop (del toolkit oficial)
1. Abrir la herramienta `JackCompiler`.
2. Seleccionar la carpeta del proyecto.
3. Se generarán automáticamente los `.vm`.

### ✔ Opción B — JackCompiler Web (recomendado)
🔗 https://www.nand2tetris.org/jack-compiler

1. Sube la carpeta completa del proyecto, incluyendo `/OS`.
2. Descarga el ZIP que contiene los `.vm`.

---

## ▶️ Cómo Ejecutar (VM → Juego)

### ✔ Opción 1: VM Emulator Desktop
1. Abrir `VMEmulator`.
2. Cargar todos los `.vm`.
3. Presionar **Run**.

### ✔ Opción 2: VM Emulator Web
🔗 https://nand2tetris.github.io/web-ide/vm

1. Sube los `.vm` generados.
2. Presiona **Run** para iniciar el juego.

---

## 🎯 Objetivos Académicos Cubiertos

Este proyecto demuestra dominio en:

- Programación en **Jack**.
- Uso del **OS del curso** (Screen, Output, Keyboard, Math, Memory).
- Diseño modular de software.
- Ciclo de juego.
- Animación básica mediante `Sys.wait()`.
- Control de teclado.
- Estructuras de datos.
- Manejo de pantalla y coordenadas.
- Creación de un videojuego funcional desde cero.

---

## 📘 Justificación del Diseño
El juego se diseñó siguiendo:

- **Modularidad estricta** → cada clase cumple un rol claro.
- **Separación de responsabilidades** → lógica, renderizado, puntaje y entradas están aislados.
- **Rendimiento óptimo** → uso eficiente de la pantalla para evitar parpadeos.
- **Simetría de columnas** → uso correcto de palabras horizontales sin colisiones.
- **Compatibilidad total con el Nand2Tetris VM**.

---

## 👤 Autores
Proyecto desarrollado por **Andrés D. Echeverri B. y Felipe Agudelo Posada**  
Evaluación Nº 4 – Organización de Computadores  
Universidad EAFIT

---

## 🎥 Video de Demostración
Mira aquí la ejecución completa del juego:

👉 
