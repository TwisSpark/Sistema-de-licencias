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

### 🔹 Nota técnica

- Este comando solo funciona si el usuario tiene una **licencia registrada**.  
- Si no tiene licencia, mostrará un mensaje indicando que debe **comprar y registrar** la licencia primero.   

---


## 🧩 Código (1/1) 

```
$nomention

$if[$varExists[licencia]==false]
$title[⚠️ Falta la variable "licencia"]
$description[Por favor, agrégala en la aplicación lo antes posible.

Pulsa el botón de abajo para ver cómo está la variable y su valor guardado.]
$addButton[yes;https://github.com/TwisSpark/Sistema-de-licencias/blob/main/variable.md;Ver;link]
$color[#e62121]
$stop
$endif 


$var[userID;$findUser[$message[1;usuario]]]
$jsonParse[$getUserVar[licencia;$var[userID]]]
$color[#ff8418]


$if[$jsonExists[licencia_activa]==false]
$ephemeral
$if[$var[userID]==$authorID]
  $title[🔴 ¡No tienes permiso de conducir! 🚫🚗]
  $description[Adquiere tu licencia en la tienda usando **-shop** y luego regístrala con </registrar_licencia:$slashID[registrar_licencia]>. ¡Sin licencia no puedes manejar!]
$else
  $title[🔴 $username[$var[userID]] no tiene licencia válida 🚫🚗]
  $description[Dile que compre una en **-shop** y que la active con </registrar_licencia:$slashID[registrar_licencia]>. ¡A conducir responsable!]
$endif

$elseif[$jsonExists[licencia_activa]==true]
 
$thumbnail[$userAvatar[$var[userID]]]
$title[¡Licencia de $nickname[$var[userID]]!]
$addField[Tu número de licencia:; $json[licencia_numero] ;no]
$addField[Nombre:; $json[nombre]  ;no]
$addField[Apellido:; $json[apellido]  ;no]
$addField[Fecha de nacimiento:; $json[fecha_de_nacimiento] ;no] 
$addField[Tipo:; $json[licencia_tipos] ;no]
$addField[Puntos:; $json[licencia_puntos]/10 ;no]
$addField[Expedición:; $json[licencia_expedicion] ;no]
$addField[Caducidad:; $json[licencia_caducidad] ;no]
$footer[$serverName[$guildID]]
$footerIcon[$serverIcon]

$endif
```