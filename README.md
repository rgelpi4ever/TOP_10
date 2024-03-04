# TOP_10
Busqueda top 10
# 1. Leer una palabra clave desde la entrada estándar
palabra_clave = input("Introduce una palabra clave: ")

# 2. Buscar la palabra clave en Google utilizando el API de SERPAPI
from serpapi import GoogleSearch

def buscar_en_google(palabra):
    # Configurar los parámetros para la búsqueda en SERPAPI
    parametros = {
        "q": palabra,
        "google_domain": "google.com",
        "hl": "es",
        "gl": "es",
        "device": "desktop"
    }

    # Realizar la búsqueda
    busqueda = GoogleSearch(parametros)
    resultados = busqueda.get_dict()

    # Extraer los títulos de los 10 primeros resultados
    titulos = [resultado['title'] for resultado in resultados['organic_results'][:10]]
    return titulos

# Obtener los títulos de los resultados del top 10
titulos_resultados = buscar_en_google(palabra_clave)

# Imprimir los títulos
print("Títulos de los resultados del top 10:")
for i, titulo in enumerate(titulos_resultados, start=1):
    print(f"{i}. {titulo}")
