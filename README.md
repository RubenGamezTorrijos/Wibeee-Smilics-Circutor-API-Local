# ⚡Wibeee Smilics & Circutor API Local XML  

| Wibeee |
|:--------:|
| ![Wibeee-logo](https://github.com/user-attachments/assets/8c8a5418-6109-4138-af2a-9ae9f6a0848b) |

| Smilics | Circutor |
|:---------:|:----------:|
| ![collage-Wibeee-01-1024x747](https://github.com/user-attachments/assets/2d748ed6-e6f4-4c33-9c0b-4d2d84fec564) | ![Wibeee_Monofasico_y_Trifasico](https://github.com/user-attachments/assets/119618e7-fc21-4350-9632-c2f426b2b2e6) |

Recopilación de datos del dispositivo **Wibeee: Smilics ó Circutor** usando conexión HTTP por el puerto 80 en modo local, para integrarlos en nuestra base de datos **InfluxDB 2.0** y monitorizarlos con herramientas **Open Source**.  

---

## 💡Introducción  

### ¿Qué es Wibeee?  
**Wibeee** es un analizador de consumo eléctrico con conexión inalámbrica vía WiFi que permite monitorizar en tiempo real e históricos del consumo eléctrico mediante dispositivos inteligentes, tablets o PCs. La comunicación utiliza el protocolo **ModBus** y lenguaje **XML**.  

### ✅Ventajas de este proyecto:  
- **Acceso local:** No dependerás de portales externos como [Circutor](http://wibeee.circutor.com) o [Smilics](https://smilics.com/wibeee).  
- **Datos en tiempo real:** Obtén información sin retardos de entre 1 a 5 minutos típicos de los fabricantes.  
- **Herramientas Open Source:** Integra los datos directamente en **Node-RED**, **InfluxDB 2.0** y **Grafana**, evitando aplicaciones propietarias.  

---

## 📋Requisitos  

### 👨🏻‍🔧Hardware  
- **PC local**, **Raspberry Pi**, **Servidor NAS**, o máquina virtual.  

### 🧑🏻‍💻Software  
- **Docker** (opcional para simplificar la instalación).  
- **Node-RED** para recopilar y transformar datos.  
- **InfluxDB 2.0** para almacenamiento.  
- **Grafana** para visualización avanzada *(opcional).*

| Wibeee monitorizado en InfluxDB 2.0 |
|:------------:|
|![Esquema_InfluxDB2 0_Wibeee_Circutor](https://user-images.githubusercontent.com/19588354/130484463-0f3d7e45-73d9-48ad-96e8-e9fe3408e90f.jpg)|


---

## 🚀Pasos para la configuración  

### 1️⃣ **Configuración de Node-RED**  

1. Instala Node-RED en tu dispositivo y accede a su portal web.  
2. Usa los nodos necesarios para obtener datos del dispositivo mediante su API local.  
3. Transforma los datos con bloques personalizados y envíalos a tu base de datos (**InfluxDB 2.0** o **MySQL**).  

| **Ejemplo de configuración en Node-RED:** |
|------------------------------------------|
|![Node-RED Ejemplo](https://user-images.githubusercontent.com/19588354/131037062-941eae52-ec44-4759-b664-f097da05b6e8.jpg)|  

#### 🔗 URLs de la API del dispositivo:  
- **Datos en tiempo real:**  
```http
http://192.168.X.X/en/status.xml
