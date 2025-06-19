# tec2025sql

Agente SQL para análisis de datos de negocio usando FastAPI, OpenAI y SQLite.

## Descripción general

Este proyecto implementa un asistente virtual que responde preguntas de negocio relacionadas con ventas, productos y distribuidores, generando y ejecutando consultas SQL sobre una base de datos local. Utiliza FastAPI para la API, OpenAI para la generación de lenguaje natural a SQL, y SQLite como base de datos.

## Estructura del proyecto

- `main.py`: API principal con FastAPI. Expone endpoints para recibir preguntas, consulta OpenAI, extrae y ejecuta SQL, y devuelve resultados interpretados y en tabla HTML.
- `create_db.py`: Script para crear y poblar la base de datos `store.db` con tablas y datos de ejemplo (productos, distribuidores, ventas).
- `prompt.txt`: Prompt base para el modelo de lenguaje, con reglas y estructura de la base de datos.
- `requirements.txt`: Lista de dependencias Python necesarias.
- `templates/index.html`: Interfaz web para interactuar con el asistente.
- `store.db`: Base de datos SQLite generada por `create_db.py`.

## Funcionamiento

1. El usuario accede a la interfaz web o realiza una petición a la API.
2. El sistema toma la pregunta, la inserta en el prompt y consulta a OpenAI.
3. Se extrae el SQL generado, se adapta a SQLite y se ejecuta sobre la base de datos local.
4. Se devuelve una interpretación, los resultados en tabla y el query SQL generado.

## Detalle de archivos

- **main.py**: Lógica de API, integración con OpenAI, ejecución de SQL y formateo de respuestas.
- **create_db.py**: Define y llena las tablas `Productos`, `Distribuidores` y `Ventas` con datos de ejemplo.
- **prompt.txt**: Define el rol del asistente, reglas de negocio y estructura de la base de datos.
- **templates/index.html**: Interfaz visual para preguntas y visualización de resultados.
- **requirements.txt**: Incluye FastAPI, Uvicorn, OpenAI, Pydantic, Jinja2, LangGraph y LangChain.

## Uso

1. Crea y activa un entorno virtual:
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```
2. Instala dependencias:
   ```bash
   pip install -r requirements.txt
   ```
3. Genera la base de datos:
   ```bash
   python create_db.py
   ```
4. Ejecuta el servidor:
   ```bash
   uvicorn main:app --reload
   ```
5. Accede a la interfaz en `http://localhost:8000`.
        