import random

def jugar_piedra_papel_tijera():
    """
    Simula una partida de piedra, papel o tijera.

    Returns:
        str: El resultado de la partida (ganaste, perdiste o empataste).
    """

    opciones = ["piedra", "papel", "tijera"]

    while True:
        usuario = input("Elige: piedra, papel, tijera (o escribe 'salir' para terminar): ").lower()

        if usuario == "salir":
            break

        if usuario not in opciones:
            print("Opción inválida. Intenta de nuevo.")
            continue

        computadora = random.choice(opciones)
        print(f"La computadora eligió: {computadora}")

        if usuario == computadora:
            print("¡Empate!")
        elif (usuario == "piedra" and computadora == "tijera") or \
             (usuario == "papel" and computadora == "piedra") or \
             (usuario == "tijera" and computadora == "papel"):
            print("¡Ganaste!")
        else:
            print("¡Perdiste!")


import random

# Opciones disponibles para el juego
opciones = ["piedra", "papel", "tijera"]

# Reglas del juego (tupla con combinaciones ganadoras)
reglas = (
    ("piedra", "tijera"),  # Piedra gana a tijera
    ("papel", "piedra"),   # Papel gana a piedra
    ("tijera", "papel"),   # Tijera gana a papel
)

# Diccionario para los resultados posibles
resultados = {
    "empate": "¡Es un empate!",
    "ganaste": "¡Ganaste!",
    "perdiste": "¡Perdiste!"
}

# Lista para guardar el historial de resultados
historial = []

def obtener_resultado(usuario, computadora):
    """
    Función para determinar el resultado del juego.
    Devuelve 'empate', 'ganaste' o 'perdiste'.
    """
    if usuario == computadora:
        return "empate"
    elif (usuario, computadora) in reglas:
        return "ganaste"
    else:
        return "perdiste"

def mostrar_historial():
    """
    Muestra el historial de resultados jugados.
    """
    if len(historial) > 0:
        print("\nHistorial de resultados:")
        for resultado in historial:
            print(f"- {resultado}")
    else:
        print("\nNo has jugado ninguna partida todavía.")

# Bucle principal del juego
while True:
    # Pedir al jugador que elija entre piedra, papel o tijera
    usuario = input("Elige: piedra, papel, tijera (o escribe 'salir' para terminar, 'historial' para ver resultados): ").lower()

    # Mostrar historial si el usuario lo pide
    if usuario == "historial":
        mostrar_historial()
        continue

    # Terminar el juego si el jugador escribe 'salir'
    if usuario == "salir":
        break

    # Verificar si la opción es válida
    if usuario not in opciones:
        print("Opción inválida. Por favor elige entre 'piedra', 'papel' o 'tijera'.")
        continue

    # La computadora elige aleatoriamente entre piedra, papel o tijera
    computadora = random.choice(opciones)
    print(f"La computadora eligió: {computadora}")

    # Determinar el resultado de la partida
    resultado = obtener_resultado(usuario, computadora)
    
    # Mostrar el resultado usando el diccionario de resultados
    print(resultados[resultado])

    # Guardar el resultado en el historial
    historial.append(resultados[resultado])
