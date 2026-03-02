# 📌 Comando de comprar licencias

## `/buy_licencias`

Comando exclusivo de tipo **Slash Command (`/`)** utilizado para comprar licencias dentro del sistema.

⚠️ **Importante:**  
Este comando solo funciona si las opciones están configuradas exactamente igual que en la imagen de ejemplo.  
Si cambias los nombres o valores, el comando no funcionará correctamente.

---

## 🔹 Opciones del Comando

### 1️⃣ Texto
- **Tipo:** String (Text)
- **Requerido:** ✅ Sí
- **Descripción:** Selecciona el tipo de licencia que deseas comprar.
- **Restricción:** Solo permite valores predefinidos (choices).

---

## 🔹 Predefined Choices

1️⃣ **Choice name:** Licencia Principal  
   **Choice value:** `7`

2️⃣ **Choice name:** Coches  
   **Choice value:** `2`

3️⃣ **Choice name:** Motos  
   **Choice value:** `3`

4️⃣ **Choice name:** Camiones  
   **Choice value:** `1`

⚠️ Debe estar escrito exactamente igual que en la imagen de ejemplo.  
Si modificas los nombres o valores, el sistema no reconocerá correctamente el tipo de licencia.

---

## 🔹 Imagen de configuración

<div align="center">
  <img src="https://i.imgur.com/Uvr78Rz.png" width="500">
</div>

---

## 🔹 Nota importante sobre el JSON

Si tienes conocimientos de JSON, puedes editar la estructura utilizada en:

```
$jsonParse
```

⚠️ Sin embargo, debes tener mucho cuidado al modificar el JSON o el código.

- Si eliminas una clave importante.
- Si cambias nombres internos.
- Si alteras la estructura sin actualizar el sistema.

El comando puede romperse y dejar de funcionar correctamente.

Si no sabes cómo editar JSON o el código, ve a mi servidor de soporte: **Sparkify World** para recibir ayuda antes de hacer cambios.

---

🔒 Este sistema depende directamente de la estructura correcta del JSON.  
Modificarlo sin conocimiento puede causar errores graves en el funcionamiento del bot.

