# Proyecto-XSD-RegEx
# Validación de Usuarios con XML y XSD

## Descripción
Este proyecto contiene un sistema de almacenamiento y validación de los datos de los usuarios diseñados previamente mediante un archivo XML (`datosUsuarios.xml`) vinculado a un esquema de validación XSD (`validacionUsuarios.xsd`).

---

## Estructura del proyecto
```
proyecto/
├── datosUsuarios.xml
└── validacionUsuarios.xsd
```

---

## Implementación

El archivo XML contiene la lista de usuarios diseñados anteriormente con sus características como: correo electrónico, número de teléfono, código postal, nombre de usuario y contraseña.

El archivo XSD valida los tipos de datos y se asegura que las restricciones sean correctas mediante expresiones regulares. La vinculación entre ambos archivos se realiza con el atributo `xsi:noNamespaceSchemaLocation` en el elemento raíz del XML:
```xml
<usuarios xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:noNamespaceSchemaLocation="validacionUsuarios.xsd">
```

---

## Restricciones aplicadas

### Correo electrónico
- **Regex:** `[a-zA-Z0-9._%+\-]+@[a-zA-Z0-9.\-]+\.[a-zA-Z]{2,}`
- **Estándar:** RFC 5321/5322
- Permite letras, dígitos y los caracteres `._%+-` antes del `@`. El dominio debe contener al menos un punto y una extensión de mínimo 2 letras.

### Número de teléfono
- **Regex:** `[6789][0-9]{8}`
- **Estándar:** Numeración oficial española (CNMC)
- Exactamente 9 dígitos. El primero debe ser 6 o 7 (móvil) o 8 o 9 (fijo).

### Código postal
- **Regex:** `(0[1-9]|[1-4][0-9]|5[0-2])[0-9]{3}`
- Exactamente 5 dígitos. Los dos primeros corresponden al código de provincia español, del 01 (Álava) al 52 (Melilla).

### Nombre de usuario
- **Regex:** `[a-z][a-zA-Z0-9_]{2,29}`
- Debe comenzar con una letra minúscula. Solo permite caracteres alfanuméricos y guión bajo. Longitud entre 3 y 30 caracteres.

### Contraseña
- **Regex:** `[a-zA-Z0-9!@#%&*?_\-+=.,;:/\\]{8,}`
- Mínimo 8 caracteres. Permite letras mayúsculas, minúsculas, dígitos y símbolos especiales.

---
