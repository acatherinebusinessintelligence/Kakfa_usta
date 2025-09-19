# 🚀 Instructivo de Instalación — Python + Podman + WSL2

Este repositorio contiene los pasos básicos para preparar un entorno de **desarrollo en Windows 11** usando:

- 🐍 **Python**
- 📦 **Podman** + **Podman Compose**
- 🐧 **WSL2 (Windows Subsystem for Linux)**

---

## ✅ Requisitos previos
- Windows 10 (2004 o superior) o Windows 11
- Virtualización habilitada en BIOS
- Conexión a internet

---

## 1️⃣ Instalación de Python

1. Descarga desde la página oficial:  
   👉 [https://www.python.org/downloads/](https://www.python.org/downloads/)

2. Ejecuta el instalador (`.exe`) y **marca la casilla** ✅ `Add Python to PATH`.

3. Haz clic en **Install Now** y espera a que termine.

4. Verifica la instalación en `cmd`:
   ```bash
   python --version
   pip --version
   ```

---

## 2️⃣ Instalación de Podman

1. Descarga Podman desde el sitio oficial:  
   👉 [https://podman.io/getting-started/installation](https://podman.io/getting-started/installation)

2. Ejecuta el instalador y sigue el asistente.  
   - Primero instalará la **GUI (dashboard)**.  
   - Luego pedirá instalar Podman en modo WSL → elige **Yes**.

3. Verifica la instalación:
   ```bash
   podman --version
   ```

4. Instala Podman Compose (requiere Python/pip):
   ```bash
   pip install podman-compose
   ```

5. Configura la variable de entorno `PATH` para que incluya el directorio donde quedó instalado `podman-compose`.

---

## 3️⃣ Instalación de WSL2

1. Abre **PowerShell como administrador**.

2. Ejecuta:
   ```bash
   wsl --install
   ```

   Esto habilitará WSL y descargará **Ubuntu** automáticamente.

3. Si tu Windows es antiguo (antes de 2004), habilita manualmente:
   ```bash
   dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
   dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
   wsl --set-default-version 2
   ```

   Reinicia el sistema.

4. Abre la Microsoft Store, busca **Ubuntu** e instálalo (si no lo tienes ya).

5. Al iniciar Ubuntu por primera vez, define tu usuario y contraseña de Linux.

6. Actualiza paquetes:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

7. Verifica:
   ```bash
   wsl --version
   ```

---

## 📜 Notas importantes
- Siempre marca la casilla **“Add Python to PATH”** en la instalación.  
- Guarda tus proyectos en el **home de Linux** (`/home/usuario/`), no en `C:\`.  
- Usa `podman ps` para verificar contenedores activos.  
- Si Podman Compose no funciona, revisa que esté en el `PATH`.

---

## 👩‍💻 Autores
- **Tatiana Cabrera**  
- **Albert Ospina**
