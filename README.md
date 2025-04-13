
# 🛡️ Mutillidae Brute Force Lab — Burp Suite & Hydra

Este repositorio documenta una práctica de análisis de vulnerabilidades sobre el sistema de autenticación de **Mutillidae**, una aplicación web deliberadamente vulnerable. Se han utilizado herramientas como **Burp Suite** e **Hydra** para simular ataques de fuerza bruta y evaluar los mecanismos de defensa del sistema.

> ⚠️ Este proyecto fue realizado **en un entorno virtual cerrado y controlado**, con fines **exclusivamente educativos** y dentro del marco de una asignatura relacionada con ciberseguridad ofensiva. Ninguna de las técnicas empleadas ha sido dirigida contra sistemas reales ni servicios en producción.

---

## 🎯 Objetivos del proyecto

- Simular un ataque de fuerza bruta sobre un sistema de login vulnerable.
- Aplicar técnicas de interceptación, análisis y automatización de peticiones HTTP.
- Comprender los riesgos de una autenticación débil y su posible explotación.
- Proponer recomendaciones de mitigación para entornos reales.

---

## 🧪 Entorno de pruebas

| Elemento              | Valor                              |
|-----------------------|-------------------------------------|
| Aplicación objetivo   | Mutillidae                          |
| Dirección IP          | `10.0.2.10`                         |
| Ruta de login         | `/mutillidae/index.php?page=login.php` |
| Usuario objetivo      | `admin`                             |
| Diccionario utilizado | Personalizado                       |
| Herramientas          | Burp Suite, Hydra                   |

---

## 🧰 Herramientas utilizadas

- **Burp Suite**: Para interceptar, analizar y manipular solicitudes HTTP.
- **Intruder (Burp)**: Para automatizar el envío de múltiples combinaciones de login.
- **Hydra**: Para realizar ataques de fuerza bruta contra formularios de autenticación vía HTTP POST.
- **Diccionario personalizado**: Generado previamente con combinaciones comunes de contraseñas.

---

## 🔄 Proceso de ataque

### 🔸 Burp Suite

1. Configuración del proxy para interceptar tráfico desde el navegador.
2. Captura de la solicitud de login con credenciales falsas.
3. Envío al módulo **Repeater** para pruebas manuales.
4. Configuración de **Intruder** con puntos de inyección y diccionario.
5. Ejecución del ataque automatizado y análisis de respuestas del servidor.

### 🔸 Hydra

1. Identificación de parámetros del formulario: `username`, `password`, `submit`.
2. Construcción del comando Hydra con método `http-post-form`.
3. Ejecución del ataque con diccionario y revisión de resultados en consola.

---

## 📉 Vulnerabilidad detectada

- **Tipo**: Autenticación débil
- **Descripción**: El sistema permite intentos de login ilimitados sin mecanismos de mitigación.
- **Impacto**: Riesgo de acceso no autorizado mediante ataques automatizados.
- **Credenciales obtenidas**: `admin : 123456` (Mutillidae default)

---

## 🔐 Recomendaciones de mitigación

- Limitar intentos de login con bloqueo temporal por IP o usuario.
- Añadir CAPTCHA o delays entre intentos.
- Habilitar autenticación multifactor (MFA).
- Registrar intentos fallidos y generar alertas.
- Aplicar políticas de contraseñas seguras.

---
