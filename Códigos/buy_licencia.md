# 📌 Comando de comprar licencias

## `/buy_licencias`

Comando exclusivo de tipo **Slash Command (`/`)** utilizado para comprar licencias dentro del sistema.

⚠️ **Importante:**  
Este comando solo funciona si las opciones están configuradas exactamente igual que en la imagen de ejemplo.  
Si cambias los nombres o valores, el comando no funcionará correctamente.

---

## 🔹 Opciones del Comando

### 1️⃣ Texto
- **Tipo:** (Text)
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
$jsonParse[
{
    "1": {
      "id": 1,
      "objeto": "Camion",
      "precio": 1500,
      "mensaje_compra": "**| Has comprado la licencia de Camion 🚛 por 1.500$**",
      "licencia_tipo": "C"},
    "2": {
      "id": 2,
      "objeto": "Coche",
      "precio": 2000,
      "mensaje_compra": "**| Has comprado la licencia de Coche 🏎 por 2.000$**",
      "licencia_tipo": "A"},
    "3": {
      "id": 3,
      "objeto": "Moto",
      "precio": 2300,
      "mensaje_compra": "**| Has comprado x1 Licencia de Moto 🏍 por 2.300$**",
      "licencia_tipo": "B"},
    "7": {
      "id": 7,
      "objeto": "Licencia Principal",
      "precio": 5300,
      "mensaje_compra": "**| Has comprado La Licencia Principal 🪪 por 5,300$** \n\nUsa </registrar_licencia:$slashID[registrar_licencia]> para activar tu licencia",
      "licencia_tipo": "true"
    }    
  }
]   
```

⚠️ Sin embargo, debes tener mucho cuidado al modificar el JSON o el código.

- Si eliminas una clave importante.
- Si cambias nombres internos.
- Si alteras la estructura sin actualizar el sistema.

El comando puede romperse y dejar de funcionar correctamente.

Si no sabes cómo editar JSON o el código, ve a mi servidor de soporte: **Sparkify World** para recibir ayuda antes de hacer cambios.


🔒 Este sistema depende directamente de la estructura correcta del JSON.  
Modificarlo sin conocimiento puede causar errores graves en el funcionamiento del bot.
---

## 🧩 Código (1/1) 

```
$nomention
$defer 
$jsonParse[
{
    "1": {
      "id": 1,
      "objeto": "Camion",
      "precio": 1500,
      "mensaje_compra": "**| Has comprado la licencia de Camion 🚛 por 1.500$**",
      "licencia_tipo": "C"},
    "2": {
      "id": 2,
      "objeto": "Coche",
      "precio": 2000,
      "mensaje_compra": "**| Has comprado la licencia de Coche 🏎 por 2.000$**",
      "licencia_tipo": "A"},
    "3": {
      "id": 3,
      "objeto": "Moto",
      "precio": 2300,
      "mensaje_compra": "**| Has comprado x1 Licencia de Moto 🏍 por 2.300$**",
      "licencia_tipo": "B"},
    "7": {
      "id": 7,
      "objeto": "Licencia Principal",
      "precio": 5300,
      "mensaje_compra": "**| Has comprado La Licencia Principal 🪪 por 5,300$** \n\nUsa </registrar_licencia:$slashID[registrar_licencia]> para activar tu licencia",
      "licencia_tipo": "true"
    }    
  }
]   
$var[dinero;$getUserVar[dentrobanco]]
$var[item;$message[1;licencia]]

$var[item_name;$json[$var[item];objeto]]
$var[item_price;$json[$var[item];precio]] 
$var[item_id;$json[$var[item];id]]
$var[item_buy_message;$json[$var[item];mensaje_compra]]
$var[standard_licensetienda;$json[$var[item];licencia_tipo]]
$var[itemExists;$jsonExists[$var[item]]]


$jsonParse[$getUserVar[licencia]]

$var[comprada_licencia;$jsonExists[comprada_licencia]]
$var[licencia_activa;$jsonExists[licencia_activa]]
$var[comprada_licencia_;$jsonExists[licencia_tipo;$var[item]]]



$if[$var[itemExists]==false]
   
    $title[❌ Ítem no encontrado]
    $description[Ese ítem no está disponible en la tienda.]
    $color[#e62121]

 
$elseif[$and[$var[item]!=7;$var[comprada_licencia]==false]==true]
  
    $title[🚫 Compra no permitida]
    $description[No puedes comprar otra licencia sin haber adquirido primero la licencia principal.]
    $color[#e62121]
     
    
$elseif[$or[$and[$var[comprada_licencia]==true;$var[item]==7]==true;$var[comprada_licencia_]==true]==true]
  
    $title[⚠️ Licencia duplicada]
    $description[Ya posees este tipo de licencia. No puedes registrarla nuevamente.] 
    $color[#e62121]     
    

$elseif[$and[$var[comprada_licencia]==true;$var[licencia_activa]==false]==true]

$title[⚠️ Licencia pendiente de activación]
$description[Ya tienes una licencia comprada, pero aún no la has activado.

Usa </registrar_licencia:$slashID[registrar_licencia]> para activar tu licencia.]
$color[#e62121] 
                  
                     
$elseif[$var[dinero]<$var[item_price]]

    $title[💰 Fondos insuficientes]
    $description[No tienes suficiente dinero en el banco para realizar esta operación.]
    $color[#e62121]
    
                
$elseif[$var[dinero]>=$var[item_price]]

    $title[✅ Compra realizada]
    $description[$var[item_buy_message]]
    $color[#ff8418]
         
    $jsonParse[$getUserVar[licencia]] 
    $if[$var[item]==7] 
    $jsonSetString[comprada_licencia;true]    
    $else     
    $jsonSetString[licencia_tipos;$json[licencia_tipos],$var[standard_licensetienda]]
    $jsonSetString[licencia_tipo;$var[item_id];$var[standard_licensetienda]]
    $endif 
 
    $setUserVar[licencia;$jsonStringify]
    $setUserVar[dentrobanco;$sub[$getUserVar[dentrobanco];$var[item_price]]]
   
    
$endif


```

