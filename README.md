# 💳 TaskBoard — Semana 10 (Validación y Form Requests)

> Proyecto integrador de **Integración de Sistemas (CE-ISC019)** — el formulario "Nueva Transacción" aprende a rechazar datos inválidos.

![Laravel](https://img.shields.io/badge/Laravel-11.x-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-8.2+-777BB4?style=for-the-badge&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-Eloquent-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

---

## 📖 Descripción

En la **Semana 10**, TaskBoard deja de confiar ciegamente en lo que recibe: se agrega **validación** al formulario "Nueva Transacción" y luego se traslada esa lógica a un **Form Request** dedicado. Abarca dos guías:

- **Jueves** — Validación directa en el controlador con `$request->validate()` y mensajes de error en la vista.
- **Viernes** — Migrar la validación a un **Form Request** (`GuardarTransaccionRequest`).

---

## ✨ Características

- ✅ Reglas de validación: `required`, `string`, `max`, `numeric`, `min`.
- ✅ Mensajes de error personalizados en español.
- ✅ Errores mostrados en la vista con `@error` y recuperación de datos con `old()`.
- ✅ Form Request propio con `authorize()`, `rules()`, `messages()` y `attributes()`.
- ✅ Controlador más limpio: la validación vive en su propia clase.

---

## 🛠️ Tecnologías

| Herramienta | Uso |
|---|---|
| **Laravel 11.x** | Framework principal |
| **Form Requests** | Validación encapsulada |
| **Blade** | Mostrar errores en el formulario |
| **MySQL** | Base de datos |

---

## 📋 Requisitos

- PHP **8.2+**, Composer y Laravel instalados
- Proyecto de la Semana 9 funcionando (formulario "Nueva Transacción" que ya guarda datos)

---

## ⚙️ Instalación

```bash
git clone https://github.com/H3CT0R503/NOMBRE-DEL-REPO.git
cd NOMBRE-DEL-REPO
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate
php artisan serve
```

Crear el Form Request:

```bash
php artisan make:request GuardarTransaccionRequest
```

---

## 🕹️ Uso

Visita `/comercios/{comercio}/transacciones/nueva` y prueba enviar el formulario:

| Caso | Resultado esperado |
|---|---|
| Monto vacío o texto | Rechazado, con mensaje de error claro |
| Nombre de cliente vacío | Rechazado, conservando lo ya escrito (`old()`) |
| Datos válidos | Transacción guardada correctamente |

---

## 📂 Estructura (relevante)

```text
app/Http/Requests/GuardarTransaccionRequest.php   # authorize(), rules(), messages(), attributes()
app/Http/Controllers/TransaccionController.php     # store() usa el Form Request
resources/views/transacciones/create.blade.php     # @error + old()
```

---

## 🧠 Conceptos aplicados

- **Validación del lado del servidor:** nunca confiar en los datos del usuario.
- **Reglas:** `required|numeric|min:0.01` para el monto, `required|string|max:255` para el nombre.
- **`old()` y `@error`:** mejor experiencia de usuario al corregir errores.
- **Form Request:** separar la validación del controlador (`authorize()` + `rules()`).
- **`authorize()`:** responde "¿puede esta persona hacer esto?" (devuelve `true`/`false`).

---

## 👤 Autor

**Hector Interiano**
📚 Integración de Sistemas · Ciclo 02-2026
🎓 UPED "Dr. Luis Alonso Aparicio" · Docente: Ing. Oscar Contreras

---

<p align="center">Hecho con 💙 y Laravel</p>
