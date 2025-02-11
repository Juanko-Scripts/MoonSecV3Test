
import platform
import psutil

def mostrar_informacion():
    # Información del sistema operativo
    sistema = platform.system()
    version = platform.version()
    arquitectura = platform.architecture()
    nombre_maquina = platform.node()

    # Información de la CPU
    cpu_frecuencia = psutil.cpu_freq().current
    cpu_logicos = psutil.cpu_count(logical=True)
    cpu_fisicos = psutil.cpu_count(logical=False)

    # Información de la memoria
    memoria = psutil.virtual_memory()
    memoria_total = memoria.total / (1024 ** 2)  # Convertir a MB
    memoria_usada = memoria.used / (1024 ** 2)    # Convertir a MB
    memoria_libre = memoria.available / (1024 ** 2)  # Convertir a MB

    # Mostrar la información
    print("Información del Dispositivo:")
    print(f"Nombre de la máquina: {nombre_maquina}")
    print(f"Sistema operativo: {sistema} {version}")
    print(f"Arquitectura: {arquitectura[0]}")
    
    print("\nInformación de la CPU:")
    print(f"Frecuencia actual: {cpu_frecuencia} MHz")
    print(f"Número de núcleos lógicos: {cpu_logicos}")
    print(f"Número de núcleos físicos: {cpu_fisicos}")

    print("\nInformación de la Memoria:")
    print(f"Memoria total: {memoria_total:.2f} MB")
    print(f"Memoria usada: {memoria_usada:.2f} MB")
    print(f"Memoria libre: {memoria_libre:.2f} MB")

if __name__ == "__main__":
    mostrar_informacion()
