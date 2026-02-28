# 📌 Comando de ver la licencia

Este comando puede usarse de **dos formas**:

1. **Comando de Slash (`/`)**  
   - Ejemplo:  
   ```text
   /ver_licencia
   /ver_licencia @Usuario
   ```
   - Permite usarlo directamente desde la interfaz de Discord con selección de opciones y menciones.

2. **Comando de Prefix (`-`)**  
   - Ejemplo:  
   ```text
   -ver_licencia
   -ver_licencia @Usuario
   ```
   - Funciona escribiendo el comando manualmente con el prefix definido en el bot.

💡 **Nota:**  
Ambas versiones hacen exactamente lo mismo: muestran la información de la licencia del usuario indicado o tu propia licencia si no se menciona ningún usuario. 

---

### 🔹 Opciones del Comando

### 1️⃣ usuario
- **Tipo:** User
- **Requerido:** ❌ No (opcional)
- **Descripción:** Especifica el usuario cuya licencia quieres consultar.  
  - Si no se indica ningún usuario, el comando mostrará tu propia licencia.
  - Se puede usar un **mencionado** o el **ID de usuario**.

<div align="center">
  <img src="https://i.imgur.com/7BZvAXg.png" width="500">
</div>

---

### 🔹 Qué muestra el comando

- **Número de licencia:** Código único de la licencia.  
- **Nombre y apellido:** Datos del propietario.  
- **Tipo de licencia:** Ej. coches, motos, camiones.  
- **Puntos:** Puntos acumulados de la licencia (máximo 10).  
- **Expedición y caducidad:** Fecha de registro y vencimiento de la licencia.  
- **Estado:** Activa o inactiva.

---

### 🔹 Ejemplo de uso

```text
/ver_licencia
```
- Muestra tu propia licencia si no se menciona ningún usuario.

```text
/ver_licencia @TwisSpark
```
- Muestra la licencia del usuario mencionado.

---

### 🔹 Nota técnica

- Este comando solo funciona si el usuario tiene una **licencia registrada**.  
- Si no tiene licencia, mostrará un mensaje indicando que debe **comprar y registrar** la licencia primero.  

```

```

