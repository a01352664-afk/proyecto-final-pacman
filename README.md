# Proyecto Final: Modificación de videojuego — Pacman

## Datos de identificación

- **Alumno:** a01352664-afk
- **Matrícula:** A01352664
- **Juego trabajado:** Pacman (librería [`freegames`](https://pypi.org/project/freegames/))
- **Rama de trabajo:** `A01352664_pacman`

## Descripción breve de los cambios realizados

Se partió de la versión original de `pacman.py` (incluida en la librería `freegames`)
y se aplicaron las tres modificaciones solicitadas:

1. **Cambio de tablero:** se reemplazó el laberinto original por un diseño propio en
   forma de "escalera/peine": tres pasillos horizontales (arriba, en medio y abajo)
   conectados por cinco pasillos verticales. El nuevo tablero se generó y verificó
   con un script auxiliar que confirma, mediante un recorrido en anchura (BFS), que
   las 115 celdas transitables están completamente conectadas entre sí y que las
   posiciones iniciales de Pacman y los 4 fantasmas siguen siendo válidas.
2. **Cambio de forma y color del alimento:** el alimento pasó de ser un punto
   blanco circular (`turtle.dot`) a un diamante de color naranja, dibujado con una
   nueva función `food(x, y)`, para que contraste más con las paredes azules del
   tablero.
3. **Fantasmas más rápidos:** se introdujo la constante `GHOST_SPEED = 10` (el doble
   de la velocidad original de 5) y se usó tanto en la posición/dirección inicial de
   los fantasmas como en las opciones de giro aleatorio al chocar con una pared, para
   que el aumento de velocidad sea consistente durante toda la partida.

Además, se tradujeron al español todos los comentarios y docstrings originales del
archivo (que estaban en inglés) para mantener consistencia en el idioma de la
documentación del código.

## Proceso seguido

1. Se clonó el repositorio y se creó un entorno virtual de Python (`python3 -m venv .venv`).
2. Se instaló la librería `freegames` (`pip install freegames`) y se copió el código
   fuente de Pacman con `python3 -m freegames copy pacman`.
3. Se creó la rama de trabajo individual `A01352664_pacman` desde `main`.
4. Se hizo un primer commit con la versión inicial del juego, sin modificar.
5. Se analizó la lógica del juego: el tablero (`tiles`) es una lista de 20x20 donde
   cada celda vale `0` (pared/vacío), `1` (pasillo con alimento) o `2` (pasillo ya
   comido); las funciones `offset()` y `valid()` traducen coordenadas de pantalla a
   índices de esa lista para decidir si un movimiento es válido.
6. Se tradujeron los comentarios a español (commit independiente).
7. Se implementó cada modificación en un commit separado, verificando en cada paso
   que el archivo compilara (`python3 -m py_compile pacman.py`) y que el juego
   arrancara sin errores.
8. Se hizo `merge` de la rama individual a `main`.
9. Se documentó el proyecto en este `README.md`.

## Cómo ejecutar el proyecto

```bash
python3 -m venv .venv
source .venv/bin/activate        # En Windows: .\.venv\Scripts\Activate.ps1
python3 -m pip install freegames
python3 pacman.py
```

Controles: flechas de dirección para mover a Pacman.
