# ⚡ Sistema de Detección de Cortes de Electricidad con Raspberry Pi

Este proyecto implementa un sistema autónomo basado en **Raspberry Pi** capaz de **detectar cortes de energía eléctrica** y **enviar notificaciones por correo electrónico**. Además, permite **controlar el sistema desde una interfaz web local**, sin necesidad de acceder a la consola. El sistema se inicia automáticamente al encender la Raspberry Pi.

---

## 📌 Características principales

- ✅ Detección en tiempo real de cortes eléctricos mediante GPIO.
- 📧 Envío automático de correo al detectar la pérdida de suministro.
- 🌐 Interfaz web (Flask) accesible desde cualquier dispositivo en la red local.
- 🔁 Inicio automático al arrancar el sistema gracias a systemd.
- 🧩 Código modular y estructura clara para facilitar mantenimiento y ampliaciones.

---

## 🗂️ Estructura del proyecto

## 🗂️ Estructura del proyecto

La estructura del repositorio es la siguiente:

``plaintext
DeteccionCortes_2.0/
├── SistemaDeteccion/           # Lógica de detección de cortes
│   └── main.py                 # Script principal que detecta cortes y envía avisos
│
├── static/                     # Archivos estáticos (CSS, imágenes...)
│   └── style.css               # Estilo de la interfaz web
│
├── templates/                  # Plantillas HTML para Flask
│   └── index.html              # Interfaz principal de control
│
├── servidor.py                 # Servidor web Flask que gestiona la activación
└── webcontrol.service          # Servicio systemd para iniciar el servidor al arrancar

---

## ⚙️ Requisitos

- Raspberry Pi con Raspbian OS.
- Python 3 instalado.
- Librerías: `flask`, `RPi.GPIO` o `gpiozero`, `subprocess`, `smtplib`.
- Conexión a internet (para el envío de correos).

---

## 🚀 Instalación y configuración

### 📁 1. Clona el repositorio

git clone https://github.com/tuusuario/DeteccionCortes_2.0.git
cd DeteccionCortes_2.0

---

### 📦 2. Instala las dependencias necesarias

pip install flask
pip install RPi.GPIO  # o gpiozero si lo prefieres

---

### ✏️ 3. Configura el script de detección

Edita el archivo `SistemaDeteccion/main.py` y añade:

- Tu dirección de correo emisor.  
- Tu contraseña o clave de aplicación.  
- El correo destinatario para recibir alertas.

---

### 🔧 4. Instala y activa el servicio systemd

sudo cp /home/pi/DeteccionCortes_2.0/webcontrol.service /etc/systemd/system/

sudo systemctl daemon-reexec  
sudo systemctl daemon-reload  
sudo systemctl enable webcontrol.service  
sudo systemctl start webcontrol.service

---

### 🌐 5. Accede a la interfaz web

Desde otro dispositivo conectado a la misma red:

http://<IP-de-tu-Raspberry>:3000

Para saber la IP de tu Raspberry:

hostname -I

