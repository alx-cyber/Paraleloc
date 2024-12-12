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
