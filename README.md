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

## Estándares y normas aplicados

Se seleccionaron y aplicaron los siguientes estándares de control de versiones
vistos en clase, y a continuación se evalúa su cumplimiento:

| Estándar aplicado | Cómo se aplicó | Evidencia | Cumplimiento |
|---|---|---|---|
| **Conventional Commits** (prefijos `feat:`, `docs:`, `fix:`, `merge:`) | Cada commit inicia con un tipo que describe la naturaleza del cambio (nueva funcionalidad, documentación, corrección o fusión), seguido de una descripción breve en modo imperativo | Historial de commits en la rama `A01352664_pacman` y en `main` (ver enlaces en el PDF de entrega) | ✅ Cumplido: los 7 commits del proyecto siguen el formato `tipo: descripción` sin excepción |
| **Rama de trabajo individual con nomenclatura `<matrícula>_<juego>`** | Se creó la rama `A01352664_pacman` desde `main` antes de iniciar cualquier modificación | `git branch` y la rama visible en GitHub | ✅ Cumplido |
| **Un commit por unidad de cambio** (nunca mezclar varias modificaciones en un solo commit) | La versión inicial, la traducción de comentarios y cada una de las 3 modificaciones solicitadas se subieron en commits separados | 7 commits distintos, cada uno con un solo propósito (`git log --oneline`) | ✅ Cumplido |
| **Integración mediante `merge` explícito a `main`** | Se hizo `git merge` de la rama individual a `main` una vez terminadas y verificadas las modificaciones | Commit de merge en `main` | ✅ Cumplido |
| **Verificación antes de cada commit** | Se corrió `python3 -m py_compile pacman.py` después de cada cambio para confirmar ausencia de errores de sintaxis antes de subirlo | Salida `OK` mostrada antes de cada commit de modificación | ✅ Cumplido |

**Limitación detectada (transparencia):** la instalación de Python de las
"Command Line Tools" de Apple en esta máquina usa Tcl/Tk 8.5.9, una versión con
un bug conocido de renderizado en pantallas Retina que impide visualizar
correctamente ventanas de `turtle` (la ventana aparece diminuta). Esto es un
problema del entorno local, no del código: el archivo compila sin errores y el
proceso corre sin excepciones. Para jugarlo visualmente sin este problema se
recomienda usar una instalación de Python más reciente (ej. desde
[python.org](https://www.python.org/downloads/), que incluye Tcl/Tk 8.6+).

## Cómo ejecutar el proyecto

```bash
python3 -m venv .venv
source .venv/bin/activate        # En Windows: .\.venv\Scripts\Activate.ps1
python3 -m pip install freegames
python3 pacman.py
```

Controles: flechas de dirección para mover a Pacman.
