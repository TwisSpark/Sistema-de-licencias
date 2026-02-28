# 📌 Comando de borrar la licencia

Este comando permite **eliminar la licencia** de un usuario registrado.  
⚠️ Por motivos de seguridad, **solo pueden usarlo los miembros del rol de staff autorizado**.

Se puede usar tanto como **Slash Command** (`/`) como **Prefix Command** (`-`).

---

## 🔹 Formas de uso

1. **Slash Command (`/`)**  
   - Ejemplo:  
   ```text
   /borrar_licencia @Usuario
   ```
   - Permite seleccionar el usuario directamente desde la interfaz de Discord.

2. **Prefix Command (`-`)**  
   - Ejemplo:  
   ```text
   -borrar_licencia @Usuario
   ```
   - Funciona escribiendo el comando manualmente usando el prefix configurado en el bot.

---

## 🔹 Opciones del Comando

### 1️⃣ usuario
- **Tipo:** User
- **Requerido:** ✅ Sí
- **Descripción:** Usuario cuya licencia será eliminada.  
  - No se puede omitir.  
  - Solo los miembros con el rol de staff autorizado pueden ejecutar el comando.

<div align="center">
  <img src="https://i.imgur.com/M75elRt.png" width="500">
</div>

---

## 🔹 Variables importantes

```js
$var[rol_staff;aquí va la id del rol staff]
```

- Esta variable define qué rol puede ejecutar el comando.  
- Solo los usuarios con este rol podrán borrar licencias, garantizando la seguridad del sistema.

---

## 🔹 Qué hace el comando

- Elimina toda la información de la licencia del usuario.  
- Restablece los valores de licencia a vacío o a estado inicial.  
- Genera un mensaje de confirmación indicando que la licencia ha sido borrada correctamente.

---

## 🔹 Nota de seguridad

- Solo los usuarios con el **rol de staff** pueden ejecutar este comando.  
- No se puede usar sin mencionar un usuario.  
- Ideal para mantener el control de licencias y evitar eliminaciones accidentales.