
from geopy.geocoders import Nominatim

def obtener_continente(latitud, longitud):
    geolocator = Nominatim(user_agent="geoapiExercises")
    location = geolocator.reverse((latitud, longitud), language='en')

    if location and 'country' in location.raw['address']:
        pais = location.raw['address']['country']
        print(f"Ubicación: {location.address}")
        print(f"País: {pais}")

        # Diccionario de continentes
        continentes = {
            'Africa': ['Nigeria', 'Sudáfrica', 'Egipto'],
            'Asia': ['China', 'India', 'Japón'],
            'Europa': ['Alemania', 'Francia', 'Reino Unido'],
            'América del Norte': ['Estados Unidos', 'Canadá', 'México'],
            'América del Sur': ['Brasil', 'Argentina', 'Chile'],
            'Oceanía': ['Australia', 'Nueva Zelanda'],
            'Antártida': ['Antártida']
        }

        # Determinar continente
        continente_encontrado = "Desconocido"
        for continente, paises in continentes.items():
            if pais in paises:
                continente_encontrado = continente
                break

        print(f"Continente: {continente_encontrado}")
    else:
        print("No se pudo determinar la ubicación.")

# Ejemplo de uso
if __name__ == "__main__":
    latitud = float(input("Introduce la latitud: "))
    longitud = float(input("Introduce la longitud: "))
    obtener_continente(latitud, longitud)
