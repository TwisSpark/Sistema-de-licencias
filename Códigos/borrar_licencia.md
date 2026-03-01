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


--- 

## 🧩 Código (1/1) 

```
$nomention
$reply
$allowUserMentions[]
$if[$varExists[licencia]==false]
$title[⚠️ Falta la variable "licencia"]
$description[Por favor, agrégala en la aplicación lo antes posible.

Pulsa el botón de abajo para ver cómo está la variable y su valor guardado.]
$addButton[yes;https://github.com/TwisSpark/Sistema-de-licencias/blob/main/variable.md;Ver;link]
$color[#e62121]
$stop
$endif  


$var[userID;$findUser[$message[1;usuario];no]]
$jsonParse[$getUserVar[licencia;$var[userID]]]
$footer[$serverName[$guildID]]
$footerIcon[$serverIcon]
$color[#ff8418] 


$var[rol_staff;1477090248239611974] $c[aquí va la id del rol staff]

$if[$roleExists[$var[rol_staff]]==false]
$title[]
$title[⚠️ Rol de staff no configurado]
$description[Es necesario configurar el rol de staff antes de usar este comando.

**Ejemplo:** `$$c[]var[rol_staff\;1477090248239611974\]`

Debes colocar únicamente la ID del rol correspondiente.]
$stop 
$endif 


$if[$hasRole[$authorID;$var[rol_staff]]==false]
$ephemeral 
$title[🔒 Acceso denegado]
$description[No tienes permisos para usar este comando. Solo el staff de $serverName[$guildID] puede ejecutar esta acción.]


$elseif[$argCount[$var[userID]]<1]
$ephemeral
$title[🔴 Usuario requerido]
$description[Debes mencionar un usuario para poder borrar su licencia.]


$elseif[$jsonExists[comprada_licencia]==false]
$ephemeral
$title[🔴 $nickname[$var[userID]] no tiene licencia válida 🚫🚗]
$description[Dile que compre una en **-shop** y que la active con </registrar_licencia:$slashID[registrar_licencia]>. ¡A conducir responsable!]


$elseif[$jsonExists[licencia_activa]==true] 
$thumbnail[$userAvatar[$var[userID]]]
$title[¡Licencia de $nickname[$var[userID]]!]
$description[Has borrado la licencia de $nickname[$var[userID]] ]
$resetUserVar[licencia;$var[userID]]


$endif


```