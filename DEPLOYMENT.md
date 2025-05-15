Guía de Despliegue para la API REST con FastAPI
Este documento describe los pasos necesarios para desplegar y ejecutar la API REST desarrollada con FastAPI y PostgreSQL.
Requisitos Previos
Python 3.7 o superior instalado.
PostgreSQL en funcionamiento y accesible con la configuración adecuada.
Acceso a la máquina virtual o servidor donde se desplegará la API.
Conexión de red abierta en el puerto que usará la API (por defecto 8000).
Pasos para Desplegar
1. Clonar el Repositorio
Clona el repositorio en tu máquina o servidor:
2. Crear y Activar un Entorno Virtual (Opcional pero recomendado)
3.  Instalar Dependencias
Instala las dependencias necesarias usando pip:
4. Configurar la Base de Datos
Asegúrate de que los datos de conexión a la base de datos en el archivo main.py estén actualizados (host, puerto, usuario, contraseña, nombre de la base de datos).
5. Ejecutar la API
Ejecuta el servidor usando Uvicorn, configurando para que escuche en todas las interfaces de red (0.0.0.0) y en el puerto 8000 (puedes cambiar el puerto si es necesario):
El parámetro --reload permite que el servidor se reinicie automáticamente al detectar cambios en el código (ideal para desarrollo).
Para producción, elimina --reload y considera usar un servidor más robusto o un proceso gestor.
7. (Opcional) Configurar Firewall y Puertos
Asegúrate de que el puerto 8000 (o el que uses) esté abierto en el firewall de la máquina virtual para aceptar conexiones externas.
