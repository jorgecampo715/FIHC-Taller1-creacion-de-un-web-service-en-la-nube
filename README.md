# Consulta de acciones con Yahoo Finance

Aplicación Python que obtiene datos históricos de acciones mediante `yfinance`. Incluye un servidor web Flask que muestra los datos en una tabla HTML y un script para consultarlos desde la terminal.

## Requisitos

- Python 3.11 o posterior
- Conexión a Internet para consultar Yahoo Finance
- Docker Desktop, si se ejecuta en contenedor

## Ejecución local

Desde la carpeta del proyecto, instala las dependencias e inicia el servidor:

```powershell
python -m pip install -r requirements.txt
python app.py
```

Abre [http://localhost:5000](http://localhost:5000) en el navegador. La página muestra los datos históricos de GOOGL desde el 1 de enero de 2020 hasta la fecha actual.

## Consulta desde la terminal

El script `read_value_yf.py` acepta el símbolo de la acción como argumento. Si no se especifica, usa GOOGL:

```powershell
python read_value_yf.py
python read_value_yf.py AAPL
```

El script imprime las filas más recientes obtenidas.

## Ejecución con Docker

Construye la imagen desde la raíz del proyecto:

```powershell
docker build -t stock-market:2.0 .
```

Inicia el contenedor y publica el puerto de Flask:

```powershell
docker run --rm -p 5000:5000 stock-market:2.0
```

Después, abre [http://localhost:5000](http://localhost:5000).

## Archivos principales

- `app.py`: servidor web Flask; la ruta `/` muestra los datos como HTML.
- `read_value_yf.py`: descarga datos mediante `yfinance` y permite su consulta desde la terminal.
- `requirements.txt`: dependencias de Python.
- `Dockerfile`: configuración para construir la imagen del contenedor.
