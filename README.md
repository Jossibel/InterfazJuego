# Diagrama de Clases del Juego de Pac-Man e Implementacion

# Descripcion:
El juego que hemos relizado es Pac-Man el cual es un juego de acción de laberintos el mismo que fue desarrollado e implusado por Namco en 1980. 
El juego trata de que el jugador controla a Pac-Man, el cual que debe comerse todos los puntos dentro de un laberinto cerrado mientras evita a cuatro fantasmas de colores. Al comer unos puntos grandes y parpadeantes llamados "Super Pildoras", los fantasmas se vuelven azules, lo que permite a Pac-Man comérselos para conseguir puntos extra.

![image](https://github.com/user-attachments/assets/2e73c5b4-1df7-4e80-8f0c-dccff2e1db74)

# Diagrama de Clases version 1.0
![352242947-b38105fd-9118-4b60-9121-23c788c15763](https://github.com/user-attachments/assets/e1c1035a-0bc9-43dd-a4ca-cf563be57839)

# Diagrama de Clases version 1.1
![DiagramaUML_Juego_PacMan](https://github.com/user-attachments/assets/7b596c69-ee6e-40e9-abb6-f3c4009dad4a)

## Descripción de las Clases

### GestorJuego
Gestiona el estado del juego, inicia y actualiza niveles, y maneja el puntaje del jugador.
- **Métodos**:
  - `iniciarJuego()`
  - `actualizar()`
  - `finJuego()`
  - `iniciarNivel(nivel: int)`
  - `actualizarPuntaje(puntos: int)`

### EstadoJuego
Define los posibles estados del juego.
- **Valores de Enumeración**:
  - `JUGANDO`
  - `FIN_JUEGO`

### Jugador

- **Atributos**:
  - `nombre: String`
  - `puntajeMaximo: int`
- **Métodos**:
  - `obtenerPuntaje()`
  - `actualizarPuntaje(puntos: int)`

### Laberinto
Genera el laberinto.
- **Métodos**:
  - `generar()`

### Pildora

- **Atributos**:
  - `puntos: int`
  - `posicion: Vector2`
- **Métodos**:
  - `comer()`

### PildoraPequeña

- Hereda las características de `Pildora`.

### SuperPildora

- **Métodos**:
  - `activarModoAsustado()`

### PacMan

- **Atributos**:
  - `velocidad: float`
  - `direccion: Vector2`
  - `posicion: Vector2`
- **Métodos**:
  - `mover()`
  - `comerPildora(pildora: Pildora)`
  - `comerSuperPildora(superPildora: SuperPildora)`
  - `morir()`

### Fantasma

- **Atributos**:
  - `velocidad: float`
  - `direccion: Vector2`
  - `posicion: Vector2`
  - `modoDisperso: boolean`
  - `modoAsustado: boolean`
- **Métodos**:
  - `mover()`
  - `perseguir()`
  - `dispersar()`
  - `huir()`

### Vector2

- **Atributos**:
  - `x: float`
  - `y: float`
- **Métodos**:
  - `Vector2(x: float, y: float)`

## Relación entre Clases

- **GestorJuego** gestiona al **Jugador**.
- **Laberinto** contiene **PildoraPequeña** y **SuperPildora**, y a **PacMan** y **Fantasma**.
- **PacMan** interactúa con **SuperPildora** para activar el modo asustado en los fantasmas.
- **Fantasmas** persiguen a **PacMan**.
- **PacMan** come **PildoraPequeña** y **SuperPildora**.

## Funcionalidad General
* GestorJuego inicia el juego (iniciarJuego()) y genera un nuevo laberinto (Laberinto.generar()).
* PacMan y Fantasma se mueven en el interior del laberinto.
* PacMan puede comer píldoras, que hace que aumente su puntaje (comerPildora()), y si come "Super píldoras" se activa el modo asustado en los fantasmas (comerSuperPildora()).
* GestorJuego actualiza el estado del juego (actualizar()), incluyendo el puntaje y el estado del jugador.
* Si PacMan es atrapado por un fantasma y ya o tiene vidas, el juego puede terminar (finJuego()).
* Por cada vez que se logre comer PacMan a los fantasmas, se ira incrementando la difcultad.
  
# Integrantes:
* Jossibel Perez
* Maria Chuico
