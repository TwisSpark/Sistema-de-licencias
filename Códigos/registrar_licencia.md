# 📌 Comando de registrar licencia

Comando de tipo Slash Command (`/`) utilizado para registrar una licencia dentro del sistema.

⚠️ Importante:
Todas las opciones del comando son obligatorias (Option Required).
El comando no funcionará si falta alguna opción.

---

## 🔹 Opciones del Comando

### 1️⃣ nombre
- Tipo: (Text)
- Requerido: ✅ Sí
- Descripción: Nombre de la persona que se registrará.

<div align="center">
  <img src="https://i.imgur.com/7O67CIP.png" width="500">
</div>


---

### 2️⃣ apellido
- Tipo: (Text)
- Requerido: ✅ Sí
- Descripción: Apellido de la persona.
<div align="center">
  <img src="https://i.imgur.com/3Zg3YzJ.png" width="500">
</div>


---

### 3️⃣ fecha_de_nacimiento
- Tipo: (Text)
- Requerido: ✅ Sí
- Descripción: Fecha de nacimiento del usuario.
- Formato recomendado: DD/MM/AAAA

<div align="center">
  <img src="https://i.imgur.com/peS93IW.png" width="500">
</div>

---

### 4️⃣ licencia_tipo
- Tipo: (Text)
- Requerido: ✅ Sí
- Descripción: Tipo de licencia que se va a registrar.
- Restricción: Solo permite valores predefinidos (choices).

#### 📌 Opciones Predefinidas (Choices)

1. Nombre mostrado: A - coches  
   Valor interno: A

2. Nombre mostrado: B - motos  
   Valor interno: B

3. Nombre mostrado: C - camiones  
   Valor interno: C

<div align="center">
  <img src="https://i.imgur.com/EgATA3J.png" width="500">
</div>
<div align="center">
  <img src="https://i.imgur.com/akvvmwo.png" width="500">
</div>


💡 Nota Técnica:
El usuario verá el nombre completo (ej: "A - coches"),
pero el sistema recibirá únicamente el valor interno (A, B o C) para su procesamiento.

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

$jsonParse[$getUserVar[licencia]]

$var[nombre;$message[nombre]]
$var[apellido;$message[apellido]] 
$var[fdn;$message[fecha_de_nacimiento]]
$var[licencia_tipo;$message[licencia_tipo]] 
$var[licencia_numero;SA-$randomString[4]-$random[1000;9999]] 
$footer[$serverName[$guildID]]
$footerIcon[$serverIcon]
$color[#ff8418]

$if[$jsonExists[comprada_licencia]==false]
$ephemeral 
$title[¡No tienes licencia aún! 🚗]
$description[Compra una en la tienda con el comando **-shop** y luego actívala con </registrar_licencia:$slashID[registrar_licencia]>.]

$elseif[$jsonExists[licencia_activa]==true]
$ephemeral 
$description[Ya tienes una licencia registrada! Usa -ver licencia para verla.]

$elseif[$jsonExists[licencia_activa]==false] 
$jsonSetString[nombre;$var[nombre]] 
$jsonSetString[apellido;$var[apellido]]
$jsonSetString[licencia_tipo;$var[licencia_tipo];$replaceText[$replaceText[$replaceText[$var[licencia_tipo];1;C];2;A];3;B]]
$jsonSetString[licencia_tipos;$replaceText[$replaceText[$replaceText[$var[licencia_tipo];1;C];2;A];3;B]]
$jsonSetString[licencia_expedicion;$day/$month/$year] 
$jsonSetString[licencia_caducidad;$day/$month/$sum[$year;10]]
$jsonSetString[licencia_numero;$var[licencia_numero]]
$jsonSetString[fecha_de_nacimiento;$var[fdn]]
$jsonSetString[licencia_puntos;10] 
$jsonSetString[licencia_activa;si] 
$setUserVar[licencia;$jsonStringify]

$author[$nickname]
$authorIcon[$authorAvatar]
$title[¡Licencia registrada exitosamente!]
$addField[Tu número de licencia:; $var[licencia_numero] ;no]
$addField[Nombre:; $json[nombre]  ;no]
$addField[Apellido:; $json[apellido]  ;no]
$addField[Tipo:; $json[licencia_tipos] ;no]
$addField[Fecha de nacimiento:; $json[fecha_de_nacimiento] ;no] 
$addField[Puntos:; $json[licencia_puntos]/10 ;no]
$addField[Expedición:; $json[licencia_expedicion] ;no]
$addField[Caducidad:; $json[licencia_caducidad] ;no]

$endif 


```
