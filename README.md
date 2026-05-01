🩺 Validador de Registros Médicos

Este proyecto es un motor de validación de datos clínicos desarrollado en Python. Permite procesar listas de registros médicos (diccionarios) y verificar que cumplan con estrictas reglas de negocio y formatos de datos antes de ser procesados por un sistema de salud.

🚀 Funcionalidades
El script realiza una validación exhaustiva en tres niveles:

Validación de Estructura de Lista: Verifica que la entrada sea una secuencia válida (lista o tupla).

Validación de Integridad: Asegura que cada registro sea un diccionario y contenga todas las claves requeridas (patient_id, age, gender, diagnosis, medications, last_visit_id).

Validación de Contenido (Reglas de Negocio):

IDs: Comprueba que los IDs de paciente y visita sigan los patrones P#### y V#### usando expresiones regulares.

Edad: Solo admite pacientes mayores de 18 años.

Género: Valida que el género sea únicamente 'male' o 'female' (sin importar mayúsculas).

Medicamentos: Verifica que se entreguen en formato de lista de textos.

🛠️ Tecnologías utilizadas
Python 3.x

Módulo re: Para el manejo de expresiones regulares (RegEx).

Comprensión de listas: Para un filtrado eficiente de registros inválidos.

Desempaquetado de diccionarios (kwargs): Para una comunicación limpia entre funciones.

📋 Ejemplo de Uso
Python
from validador_datos_medicos import validate

# Ejemplo de datos a validar
medical_records = [
    {
        'patient_id': 'P1001',
        'age': 34,
        'gender': 'Female',
        'diagnosis': 'Hypertension',
        'medications': ['Lisinopril'],
        'last_visit_id': 'V2301',
    }
]

# Ejecutar validación
if validate(medical_records):
    print("Datos listos para procesar.")
else:
    print("Error: Revisa los mensajes en consola.")
⚠️ Detección de Errores
Si un registro contiene datos incorrectos, el programa informará el error específico y su posición:

Unexpected format 'age: 15' at position 2.
Invalid format: {...} at position 3 has missing and/or invalid keys.
