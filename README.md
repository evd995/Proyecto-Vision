# Proyecto-Vision

## Estructura de archivos

- Proyecto-Vision
  - **CÓDIGO**
  - [`dlib_detector.py`](main_deteccion.py): Código necesario para calcular los bounding boxes usando dlib
    - TO-DO: completar función `get_boxes`
  - [`retinaface_detector.py`](main_deteccion.py): Código necesario para calcular los bounding boxes usando RetinaFace
    - TO-DO: completar función `get_boxes`
  - [`main_deteccion.py`](main_deteccion.py): Procesar un video y crear los archivos correspondientes
    - TO-DO: completar funcion `process_video`
  - **CARPETAS**
  - `Videos`: Descargar de [drive](https://drive.google.com/drive/u/0/folders/1hHkDDtzuCoWAveTURGSAOugUBFF9jBZ7) y colocar en esta carpeta, también está el video como numpy array [acá](https://drive.google.com/open?id=1lNAghhACUCktvsMljfRoHyFYzB4FPHiW)
  - `Deteccion`:
    - (Nombre de metodo de detección): Puede ser `RetinaFace` o `dlib`
      - (Nombre de video)
        - (Número de frame)
          - `bounding_boxes.npy`: Matriz donde las filas sean los bounding boxes de las caras, y las columnas sean: coordenada x de esquina sup izquierda, coordenada y de esquina sup izquierda, ancho y alto (en este orden)
          - `Faces`: Carpeta con caras croppeadas (nombre tiene que ser `xx.jpg`, donde `xx` es el número de fila en `bounding_boxes.npy`)
          - `descriptores.npy`: Cada fila es un descriptor obtenido con arcface de una de las caras (deben ser en el mismo orden de las caras en `bounding_boxes.npy`)
          - `landmarks.npy`: Lista donde cada entrada corresponde a la cara correspondiente de `bounding_boxes.npy`
          - `emociones.npy`: Cada fila es un individuo y cada columna una de las emociones (deben ser en el mismo orden de las caras en `bounding_boxes.npy`)
          - `headpose.npy`: Cada fila es un individuo y cada columna una de las direcciones del headpose (deben ser en el mismo orden de las caras en `bounding_boxes.npy`)
          - `interacciones_headpose.npy`: Lista de tuplas de interacciones que indican que persona en la foto interactuó con quien (Ej: [(p1, p2), (p3, p4)] indica que p1 interactuó con p2 y p3 con p4) CADA ENTRADA EN LA TUPLA CORRESPONDE AL NUMERO DE FILA DE LA PERSONA EN `bounding_boxes.npy`
          - `identidades.npy`: (Se calcula al final final) Lista que asocia cada una de las filas de `bounding_boxes.npy` con una identidad de una persona (ej: Tony Stark)
  - `Personas`
    - (Nombre de metodo de detección): Puede ser `RetinaFace` o `dlib`
      - (persona_xxx.npy): recolecta todos los descriptores de una persona en particular
