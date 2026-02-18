# 🖐️ Bio3D

![Status](https://img.shields.io/badge/status-beta-orange)
![Platform](https://img.shields.io/badge/platform-browser--only-blue)
![Offline](https://img.shields.io/badge/offline-supported-success)
![ThreeJS](https://img.shields.io/badge/3D-Three.js-black)
![MediaPipe](https://img.shields.io/badge/Hand%20Tracking-MediaPipe-blueviolet)
![AI
Vision](https://img.shields.io/badge/Computer%20Vision-RealTime-informational)

**Bio3D** es un visor 3D interactivo controlado mediante seguimiento de
mano en tiempo real, ejecutado completamente en el navegador usando
**Three.js** y **MediaPipe Hands**.

Permite rotar, hacer zoom y desplazar modelos 3D utilizando únicamente
gestos naturales con la mano, sin dispositivos adicionales.

------------------------------------------------------------------------

## 📜 Licencia

**Todos los derechos reservados**

Este proyecto no es Open-Source y fue desarrollado con fines
demostrativos y experimentales.

------------------------------------------------------------------------

## 🖥️ Demo

<div align="center">

[¡Proba ahora aquí!](https://AngelDev2343.github.io/Bio3D)

![demo](https://github.com/AngelDev2343/land/blob/main/gifs/3d1.gif?raw=true)

</div>

------------------------------------------------------------------------

## 🎯 Objetivo del proyecto

Bio3D nace como un experimento técnico con un enfoque claro:

> Explorar la interacción humano-computadora basada en visión artificial
> directamente desde el navegador.

Demuestra que es posible crear experiencias 3D avanzadas y control
gestual en tiempo real sin backend, sin instalaciones y sin software
adicional.

------------------------------------------------------------------------

## 🧠 Arquitectura general

El sistema está dividido en tres bloques principales:

### 1️⃣ Renderizado 3D

-   Motor: **Three.js**
-   Cámara perspectiva
-   Iluminación dinámica
-   Carga de modelos `.glb` / `.gltf`
-   Normalización automática de escala
-   Sistema de suavizado (LERP)

### 2️⃣ Seguimiento de mano

-   Motor: **MediaPipe Hands**
-   Detección en tiempo real desde webcam
-   Modelo ligero (`modelComplexity: 0`)
-   Una sola mano activa

### 3️⃣ Sistema de interacción

-   Mano abierta → Rotación + Zoom
-   Puño cerrado → Paneo (Arrastrar)
-   Zoom basado en tamaño relativo de la mano
-   Movimiento suavizado mediante interpolación física

Todo ocurre en el navegador.

Sin servidores.\
Sin almacenamiento externo.\
Sin procesamiento en la nube.

------------------------------------------------------------------------

## 🖐️ Sistema de gestos

### 🖐️ Mano abierta --- Rotar + Zoom

-   La posición horizontal controla rotación Y
-   La posición vertical controla rotación X
-   El tamaño de la mano controla la distancia de cámara

Zoom calculado usando:

Distancia muñeca → punta del dedo medio

Mano más grande = más cerca de la cámara\
Mano más pequeña = más lejos

------------------------------------------------------------------------

### ✊ Puño cerrado --- Arrastrar (Pan)

Cuando el sistema detecta que el meñique está plegado:

-   Se activa modo desplazamiento
-   Se mueve el grupo 3D en eje X/Y
-   Se desactiva rotación y zoom

------------------------------------------------------------------------

## 📦 Carga de modelos

Formatos soportados:

-   `.glb`
-   `.gltf`

Proceso automático:

1.  Eliminación del modelo anterior
2.  Cálculo del bounding box
3.  Normalización de escala
4.  Centrado del modelo
5.  Inserción en el grupo principal

Incluye un modelo base si no se carga ningún archivo.

------------------------------------------------------------------------

## 🎨 Interfaz

Incluye:

-   HUD de estado
-   Indicador de gesto activo
-   Visualización del esqueleto de la mano
-   Indicador porcentual de tamaño de mano
-   Botón para cargar modelo
-   Botón para resetear vista

El canvas de MediaPipe se superpone al render 3D con transparencia
parcial.

------------------------------------------------------------------------

## ⚙️ Rendimiento

-   Modelo de detección en modo ligero
-   Render optimizado con antialias
-   Interpolación suave para evitar jitter
-   Vanilla JS + ES Modules

------------------------------------------------------------------------

## 🔐 Privacidad

-   No se almacenan imágenes
-   No se envían datos a servidores
-   No hay backend
-   No hay cuentas
-   Procesamiento completamente local

------------------------------------------------------------------------

## 💻 Requisitos recomendados

-   Webcam funcional
-   2GB RAM recomendados
-   Navegador actualizado

------------------------------------------------------------------------

## 🌍 Compatibilidad

Navegadores recomendados:

-   ✅ Google Chrome
-   ✅ Microsoft Edge
-   ✅ Safari
-   ✅ Firefox
-   ✅ Vivaldi

------------------------------------------------------------------------

## 🛠️ Estado del proyecto

-   Estado: Terminado
-   Naturaleza: Experimental
-   Enfoque: Investigación en interacción 3D basada en visión

------------------------------------------------------------------------

## 🙏 Créditos

-   **Three.js** --- Renderizado 3D
-   **MediaPipe Hands** --- Seguimiento de mano
-   WebGL --- Aceleración gráfica en navegador

------------------------------------------------------------------------

## ❓ FAQ

### ¿Se almacenan modelos?

No, se cargan temporalmente en memoria.

### ¿Se guardan imágenes de la cámara?

No. El procesamiento es temporal y local.
