# Ajedrez
# Práctica Ajedrez en Realidad Virtual (VR)

## 📌 Descripción general

Este proyecto consiste en una **mejora y ampliación de una práctica previa** basada en un tablero de ajedrez en 3D desarrollado con **Three.js**. En esta versión se han incorporado **funcionalidades avanzadas de Realidad Virtual (VR)**, interacción mediante controladores, modelos 3D reales y un sistema de físicas realista utilizando **Ammo.js**.

El objetivo principal es permitir al usuario **interactuar de forma natural con las piezas de ajedrez dentro de un entorno VR**, pudiendo cogerlas, moverlas, soltarlas y desplazarse libremente por la escena.

---

## 🧩 Tecnologías utilizadas

* **Three.js** – Renderizado 3D
* **WebXR** – Soporte para Realidad Virtual
* **Ammo.js** – Motor de físicas
* **GLTF / GLB** – Modelos 3D de las piezas
* **Tween.js** – Animaciones suaves
* **Lil-GUI** – Panel de control y depuración

---

## 🕶️ Extensión de Realidad Virtual (VR)

Se ha añadido compatibilidad completa con VR mediante **WebXR**, permitiendo:

* Entrada en modo VR mediante el botón `VRButton`.
* Uso de **dos mandos VR** (izquierdo y derecho).
* Visualización de los modelos reales de los controladores.
* Movimiento y rotación del usuario dentro del escenario.

La cámara se encuentra dentro de un objeto tipo **dolly**, lo que facilita el desplazamiento del jugador por la escena sin afectar a la orientación natural de la cabeza.

---

## ✋ Interacción: Grab (agarrar objetos)

Se ha implementado un sistema de **grab** que permite coger las piezas de ajedrez usando el **mando derecho**:

* Al pulsar el **trigger** del mando derecho (`selectstart`), se activa la detección de agarre.
* Si la mano se encuentra dentro del radio de acción de una pieza, esta se puede coger.
* Mientras la pieza está siendo sostenida:

  * Su posición sigue la del mando.
  * Se sincroniza la posición gráfica con el cuerpo físico (Ammo.js).
  * **La pieza reduce su tamaño** para mejorar la visibilidad y sensación de agarre.
* Al soltar el trigger (`selectend`):

  * La pieza recupera automáticamente su **escala original**.

Este sistema simula de forma intuitiva la manipulación de objetos en VR.

---

## ♟️ Modelos 3D (GLB)

Las piezas de ajedrez utilizan **modelos 3D en formato `.glb`**, uno para cada tipo de pieza:

* Peón
* Torre
* Caballo
* Alfil
* Reina
* Rey

Los modelos se cargan dinámicamente mediante **GLTFLoader** y se reutilizan para mejorar el rendimiento. Cada pieza adapta su escala y posición para encajar correctamente con su collider físico.

Además, se ha añadido un **escenario 3D de fondo** (modelo externo) para enriquecer la ambientación.

---

## ⚙️ Sistema de físicas con Ammo.js

El proyecto emplea **Ammo.js** para dotar de realismo a la escena:

* Las piezas y el tablero cuentan con **cuerpos rígidos**.
* Se aplica gravedad y colisiones realistas.
* Las piezas pueden caerse, chocar entre sí o ser eliminadas si quedan en posiciones inválidas.
* El tablero actúa como superficie estática.

Esto permite una interacción mucho más natural y coherente con el entorno.

---

## 🎮 Controles en VR

### 🕹️ Mando derecho

* **Trigger**: agarrar y soltar piezas.
* Interacción directa con los objetos del tablero.

### 🕹️ Mando izquierdo

* **Joystick**: desplazamiento horizontal por la escena (ejes X y Z).
* **Botón inferior (X)**: bajar la altura del jugador.
* **Botón superior (Y)**: subir la altura del jugador.

Esto permite ajustar la perspectiva y adaptarse a diferentes alturas o situaciones dentro del entorno VR.

### 🔄 Reset de la escena

* Con uno de los botones del mando contrario (X o Y, según el dispositivo), se puede **reiniciar el tablero** y volver al estado inicial.

---

*Proyecto desarrollado por Raúl .... y Eva Yuan Robaina Navarro*
