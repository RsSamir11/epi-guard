# EPI-GUARD

**Verificador de casco de seguridad mediante clasificación de imágenes con Inteligencia Artificial**

Proyecto: *Tarea 04 — Desarrollo y publicación en la nube de un sistema de clasificación de imágenes mediante Inteligencia Artificial*

Autor: **Roits Samir Altamirano Martinez**
Carrera: Ing. Software con Inteligencia Artificial — SENATI

---

## ¿Qué hace?

La aplicación abre la webcam del navegador y verifica en tiempo real si la persona que aparece en pantalla está usando el casco de seguridad de forma correcta.

- Detecta los rostros presentes en el cuadro.
- Recorta la zona de la cabeza y la clasifica con un modelo de IA.
- Muestra el veredicto (**CON CASCO**, **CASCO MAL PUESTO**, **SIN CASCO**) con su porcentaje de confianza.
- Si la persona no está usando el implemento correctamente, suena una **alarma**.
- Permite **capturar** la imagen actual con la detección dibujada.
- Lleva un registro de lecturas y estadísticas de la sesión.

## Cómo se entrenó el modelo

1. Se capturaron **336 fotografías** propias con la webcam (112 por clase) y se organizaron en tres carpetas dentro de `fotos/`:
   - `sin casco/`
   - `casco puesto/`
   - `casco mal puesto/`
2. El dataset se cargó en **Teachable Machine** (Google) y se entrenó un clasificador de imágenes de 224×224.
3. El modelo se exportó a **TensorFlow.js** y se publicó en la carpeta `models/mi-modelo/` para cargarlo desde el navegador.

## Stack técnico

| Componente | Tecnología |
|---|---|
| Entrenamiento del modelo | Teachable Machine (Transfer Learning) |
| Inferencia en el navegador | TensorFlow.js + @teachablemachine/image |
| Detección de rostros | BlazeFace (TensorFlow.js) |
| Interfaz | HTML5 + CSS3 + JavaScript vanilla |
| Publicación | GitHub Pages |

## Ejecutar en local

```bash
python3 -m http.server 8080
```

Luego abrir <http://localhost:8080>.

> Es importante servirlo por HTTP: los navegadores no permiten acceder a la webcam desde `file://`.

## Publicación

La aplicación está publicada en GitHub Pages y es 100% client-side: no hay servidor propio, el modelo se descarga y ejecuta en el navegador del usuario.

## Estructura

```
├── index.html          → interfaz de la aplicación
├── css/app.css         → estilos (tema oscuro EPI-GUARD)
├── js/app.js           → lógica de detección, sonido y estadísticas
├── models/mi-modelo/   → modelo entrenado exportado a TensorFlow.js
├── fotos/              → dataset usado para el entrenamiento
└── img/                → logo institucional
```
