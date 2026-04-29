---
title: "Agenda basica CLI en Python"
version: "0.1"
date: "29/04/26"
---
# spec.md - Especificacion funcional

## 1. Descripcion general
La aplicacion es una herramienta de linea de comandos (CLI) escrita en lenguaje Python que permite gestionar una agenda de contactos almacenada en una base de datos MySQL. Ofreciendo operaciones propias de CRUD

## 2. Funcionalidades
- Crear, listar, actualizar y eliminar contactos
- Buscar contacto por nombre, por telefono y por email
- Listar todos los contactos
- Crear un menu de opciones
- CLI sea interactiva
- Almacene informacion en una base de datos MySQL

## 3. Modelos de datos

Tabla contacto en base de datos MySQL.
| Campo | Tipo | Obligatorio | Descripcion |
|-------|------|-------------|-------------|
| id | INT AUTOINCREMENT | YES | Identificador unico |
| name | VARCHAR(100) | YES | nombre contacto |
| surname | VARCHAR(200) | NO | apellidos contacto |
| tel1 | INTEGER | YES | Telefono contacto 1 |
| tel2 | INTEGER | NO | Telefono contacto 2 |
| email | VARCHAR(100) | NO | email contacto |
| note | TEXT | NO | Informacion contacto |

## 4. Casos de uso
### CU-01: Añadir contacto
1. El usuario selecciona "Añadir contacto"
2. El sistema pide: Nombre (name) surname, numero (tel1), tel2, email, notes
3. El usuario introduce los datos
4. El sistema valida los datos
5. El sistema comprueba si existe un contacto con el mismo telefono
6. El sistema el contacto en la base de datos y te muestra el id con los datos del contacto

** Flujo Alternativo A ** (validacion falla)
- El sistema muestra un mensaje de error y solicita corregir el error
** Flujo Alternativo B ** (validacion correcta)
- El sistema inserta los datos en una base de datos
** Flujo Alternativo C ** (contacto duplicado)
- El sistema nos advierte de que existe el contacto y pide confirmacion de guardado

### CU-02: Ver contacto
1. El usuario selecciona "Ver contacto"
2. El sistema pide: Nombre (name), Apellido (surname) o telefono (tel)
3. El usuario introduce los datos
4. El sistema comprueba si existe coincidencias con un LIKE en name, surname, tel1
5. El sistema muestra todos los resultados coincidentes con ese nombre

** Flujo Alternativo A ** (validacion falla)
- El sistema muestra un mensaje de error y solicita corregir el error
** Flujo Alternativo B ** (validacion correcta)
- El sistema comprueba los datos en la base de datos
** Flujo Alternativo C ** (contacto duplicado)
- El sistema nos advierte de que existe el contacto y pide confirmacion de guardado

### CU-03: Eliminar contacto
1. El usuario selecciona "Eliminar contacto"
2. El sistema pide: Nombre (name), Apellido (surname) o telefono (tel)
3. El usuario introduce los datos
4. El sistema comprueba si existe coincidencias con un LIKE en name, surname, tel1
5. El sistema muestra todos los resultados coincidentes con ese nombre

### CU-04: Editar contacto
1. El usuario selecciona "Editar contacto"
2. El sistema pide: Nombre (name), Apellido (surname) o telefono (tel)
3. El usuario introduce los datos
4. El sistema comprueba si existe coincidencias con un LIKE en name, surname, tel1
5. El sistema muestra todos los resultados coincidentes con ese nombre

### CU-05: Listar contactos
1. El usuario selecciona "Listar contactos"
2. El sistema pide: Nombre (name), Apellido (surname) o telefono (tel)
3. El usuario introduce los datos
4. El sistema comprueba si existe coincidencias con un LIKE en name, surname, tel1
5. El sistema muestra todos los resultados coincidentes con ese nombre
