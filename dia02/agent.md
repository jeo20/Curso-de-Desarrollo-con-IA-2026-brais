# agent.md

## Descripción
Este archivo documenta la arquitectura, convenciones y funcionamiento general del proyecto Django de Gestion de Usuario de E-sidif. Sirve como guía para desarrolladores que trabajen en el sistema.

---

## 1. Stack Tecnológico
- Python
- Django
- Bootstrap (frontend)
- jQuery (opcional)
- Base de datos (PostgreSQL / SQLite)

---

## 2. Estructura del Proyecto
```
project/
│
├── manage.py
├── project/
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
├── apps/
│   ├── app1/
│   │   ├── admin.py
│   │   ├── apps.py
│   │   ├── models.py
│   │   ├── views.py
│   │   ├── services.py
│   │   ├── forms.py
│   │   ├── urls.py
│   │   ├── templates/
│   │   └── static/
│   └── app2/
│
├── templates/
│   	└── base.html
│   	└── app1/
│		├── components/
│		│   ├── navbar.html
│		│   └── modals.html
│   	├── registration/
│       │   ├── login.html
│       │   ├── password_reset_complete.html
│       │   ├── password_reset_confirm.html
│       │   ├── password_reset_done.html
│       │   └── password_reset_form.html
├── static/
│   	└── css/
│   	└── img/	
│   	└── manuales/	

└── requirements.txt
```

---

## 3. Convenciones del Proyecto

### 3.1 Modelos
- Usar nombres en singular.
- Definir `__str__` en todos los modelos.
- Usar `choices` para campos con valores limitados.

### 3.2 Vistas
- Preferir Class-Based Views cuando sea posible.
- Separar lógica de negocio en servicios.
- Validar datos siempre antes de guardar.

### 3.3 Formularios
- Usar `ModelForm` cuando aplique.
- Aplicar clases de Bootstrap mediante `widgets`.

### 3.4 Templates
- Usar una plantilla base (`base.html`).
- Dividir en bloques reutilizables:
  - `title`
  - `content`
  - `extra_js`

---

## 4. Flujo General
1. Usuario realiza una petición.
2. URL dirige a una vista.
3. La vista procesa lógica y consulta modelos.
4. Se renderiza un template o se devuelve JSON.

---

## 5. Manejo de Base de Datos
- Usar migraciones (`makemigrations`, `migrate`).
- Evitar queries innecesarias (usar `select_related`, `prefetch_related`).

---

## 6. Autenticación y Permisos
- Usar sistema de autenticación de Django.
- Implementar decoradores como:
  - `login_required`
  - permisos personalizados

---

## 7. Buenas Prácticas
- Mantener código modular.
- Evitar lógica en templates.
- Documentar funciones complejas.
- Usar variables de entorno para configuración sensible.

---

## 8. Comandos Útiles
```
python manage.py runserver
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
```

---

## 9. Deploy
- Configurar `DEBUG = False`.
- Definir `ALLOWED_HOSTS`.
- Usar servidor WSGI (Gunicorn / uWSGI).
- Configurar archivos estáticos.

---

## 10. Notas Finales
Este documento debe mantenerse actualizado a medida que evoluciona el proyecto.

