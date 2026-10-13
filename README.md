# Física 2 · Unidad 1: Campo eléctrico y potencial

Proyecto de Física 2 con interfaz web (HTML + CSS + JavaScript) y cálculos en Python (Flask).

Módulos: (1) visualizador de cargas puntuales, (2) calculadora de potencial, (3) simulador de trayectoria.
El visualizador se dibuja en el navegador para que arrastrar cargas sea fluido; la calculadora y la trayectoria se calculan en Python.

## Cómo abrirlo en Visual Studio Code

1. Instala **Python 3.9 o superior** (python.org/downloads). En Windows marca *Add python.exe to PATH*.
2. Instala **Visual Studio Code** y, dentro de él, la extensión **Python** (de Microsoft).
3. Descomprime el ZIP y abre la carpeta con **Archivo → Abrir carpeta**.
4. Abre una terminal en VS Code (**Terminal → Nueva terminal**) e instala las librerías:
   ```
   pip install -r requirements.txt
   ```
   (Si `pip` no se reconoce: `python -m pip install -r requirements.txt`. En Mac/Linux usa `python3` y `pip3`.)
5. Ejecuta el proyecto de una de estas dos formas:
   - Abre `app.py` y pulsa el triángulo ▷ de arriba a la derecha, o pulsa **F5**.
   - En la terminal: `python app.py`
6. Se abre el navegador en **http://127.0.0.1:5000**. Si no se abre solo, copia esa dirección en el navegador.
7. Para detener el servidor, pulsa `Ctrl + C` en la terminal.

Opcional, recomendado: crea un entorno virtual antes del paso 4 con `python -m venv .venv` y actívalo
(Windows: `.venv\Scripts\activate`, Mac/Linux: `source .venv/bin/activate`).

## Estructura

```
unidad1_campos_electricos/
├── app.py              # servidor Flask y rutas /api/potencial y /api/trayectoria
├── fisica.py           # núcleo físico: campo(), potencial_en_punto(), trayectoria()
├── requirements.txt
├── templates/
│   └── index.html      # estructura de la página
├── static/
│   ├── css/style.css   # estilos (tema claro y oscuro)
│   └── js/app.js       # interfaz: visualizador, pestañas, llamadas a Python
├── tests/
│   └── test_fisica.py  # pruebas de validación
└── .vscode/launch.json # configuración para ejecutar con F5
```

## Pruebas automáticas

```
python -m unittest discover -s tests -v
```

## Problemas frecuentes

| Problema | Solución |
|---|---|
| `ModuleNotFoundError: No module named 'flask'` | Falta instalar las librerías (paso 4) o VS Code usa otro Python. Usa `Ctrl+Shift+P → Python: Select Interpreter`. |
| El navegador muestra «No se puede acceder a este sitio» | El servidor no está corriendo. Revisa que la terminal diga *Running on http://127.0.0.1:5000*. |
| `Address already in use` | Otro programa usa el puerto 5000. Cierra la otra ventana o cambia `PUERTO` al final de `app.py`. |
| Aparece «No se pudo calcular» en la página | El servidor de Python se detuvo. Vuelve a ejecutar `app.py` y recarga la página (F5). |
