# 🚗 Sistema-de-licencias

Sistema avanzado de licencias basado en una **variable JSON**, diseñado para gestionar registro, compra, verificación y eliminación de licencias dentro de tu bot.

Incluye guía de uso y documentación completa de cada comando.

---

## 📦 Variable JSON

La variable JSON es **obligatoria** para que el sistema funcione correctamente.  
Toda la información de las licencias se almacena y gestiona desde esta estructura.

🔎 Ver configuración de la variable aquí:  
👉 [VER VARIABLE JSON](https://github.com/TwisSpark/Sistema-de-licencias/blob/main/variable.md)

---

## 📌 Comandos del Sistema

### 🔹 /registrar_licencia

<div align="center">
  <img src="https://i.imgur.com/uIDl7ot.png" width="500">
</div>

Comando de tipo **Slash Command (`/`)** utilizado para registrar y activar una licencia previamente comprada.

👉 [Ver código /registrar_licencia](https://github.com/TwisSpark/Sistema-de-licencias/blob/main/C%C3%B3digos%2Fregistrar_licencia.md)

---

### 🔹 /ver_licencia
Permite consultar la licencia de un usuario o la propia, mostrando número, tipo, puntos, expedición y caducidad.

<div align="center">
  <img src="https://i.imgur.com/oaNI8tr.png" width="500">
</div>
👉 [Ver código /ver_licencia](https://github.com/TwisSpark/Sistema-de-licencias/blob/main/C%C3%B3digos%2Fver_licencia.md)

---

### 🔹 /borrar_licencia
Permite eliminar la licencia de un usuario registrado.  
⚠️ Disponible únicamente para el rol de staff autorizado.

👉 [Ver código /borrar_licencia](https://github.com/TwisSpark/Sistema-de-licencias/blob/main/C%C3%B3digos%2Fborrar_licencia.md)

---

### 🔹 /buy_licencias
Comando de tipo **Slash Command (`/`)** utilizado para comprar licencias dentro del sistema (Licencia Principal, Coches, Motos, Camiones).

👉 [Ver código /buy_licencias](https://github.com/TwisSpark/Sistema-de-licencias/blob/main/C%C3%B3digos%2Fbuy_licencia.md)

---

## ⚠️ Nota Importante

Este sistema depende completamente de la correcta estructura del **JSON interno**.  

Modificar:
- Nombres de claves
- Valores internos
- Choices del slash command
- IDs de roles

Puede provocar que el sistema deje de funcionar correctamente.

Si no tienes experiencia editando JSON o código, es recomendable no modificar la estructura sin asesoría previa.

---

# 💜 Únete a Sparkify World

Si quieres proponer ideas, mejorar sistemas o aportar nuevos comandos para tu bot:

👉 https://discord.gg/fPHkWuDbk9  

En **Sparkify World** puedes:

- 💡 Dar sugerencias para nuevos proyectos y sistemas  
- 🛠 Proponer comandos personalizados  
- 🚀 Ayudar en futuras actualizaciones  
- 🌍 Ser parte activa del crecimiento del proyecto  

Aquí no eres espectador.  
Eres parte de la evolución.