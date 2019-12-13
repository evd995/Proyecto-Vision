# Contenido

Esta carpeta deberá contener los archivos procesados de los atributos (Descriptores, headpose, etc). Se estructurará _por frame_, es decir, se creará una carpeta para cada frame del video y esta carpeta contendrá la info de todos los atributos de la gente en el frame

# Archivos

Los archivos ya procesados se pueden descargar [acá](https://drive.google.com/open?id=191isDWFmHhIE9IEZOtp2H2OZjW3FT3nx)

# Estructura

- `Deteccion`:
  - (Nombre de metodo de detección): Puede ser `RetinaFace` o `dlib`
    - (Nombre de video)
      - (Número de frame)
        - `bounding_boxes.npy`: Matriz donde las filas sean los bounding boxes de las caras, y las columnas sean: coordenada x de esquina sup izquierda, coordenada y de esquina sup izquierda, ancho y alto (en este orden)
        - `descriptores.npy`: Cada fila es un descriptor obtenido con arcface de una de las caras (deben ser en el mismo orden de las caras en `bounding_boxes.npy`)
        - `landmarks.npy`: Lista donde cada entrada corresponde a la cara correspondiente de `bounding_boxes.npy`
        - `emociones.npy`: Cada fila es un individuo y cada columna una de las emociones (deben ser en el mismo orden de las caras en `bounding_boxes.npy`)
        - `headpose.npy`: Cada fila es un individuo y cada columna una de las direcciones del headpose (deben ser en el mismo orden de las caras en `bounding_boxes.npy`)
        - `interacciones_headpose.npy`: Lista de tuplas de interacciones que indican que persona en la foto interactuó con quien (Ej: [(p1, p2), (p3, p4)] indica que p1 interactuó con p2 y p3 con p4) CADA ENTRADA EN LA TUPLA CORRESPONDE AL NUMERO DE FILA DE LA PERSONA EN `bounding_boxes.npy`
        - `identidades.npy`: (Se calcula al final final) Lista que asocia cada una de las filas de `bounding_boxes.npy` con una identidad de una persona (ej: Tony Stark)
