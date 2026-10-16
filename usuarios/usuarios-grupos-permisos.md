# Gestión de Usuarios, Grupos y Privilegios · Sierra Norte Padel Pro S.L.

En este documento se detalla la configuración de seguridad aplicada en Odoo bajo el principio de **mínimo privilegio**, garantizando que cada miembro del equipo acceda únicamente a las herramientas necesarias para su puesto.

## 1. Usuarios Internos Creados en Odoo
* **Jose Luis Martin Blanco** (`admin@padelpro.es`)
  * **Puesto:** Gerencia y Administración del Sistema.
  * **Tipo de Usuario:** Interno (Superadministrador).
  * **Privilegios:** Acceso completo a todos los módulos, ajustes y parametrización de la base de datos de Odoo.
* **Elena Vargas** (`evargas@sierranortepadel.es`)
  * **Puesto:** Responsable de Ventas y Logística / Almacén.
  * **Tipo de Usuario:** Interno.
  * **Privilegios:** Permisos de administración en el módulo de Ventas y en Cadena de Suministro/Inventario (necesarios para validar los albaranes de salida de stock). Sin acceso a contabilidad.
* **Carlos Méndez** (`administracion@sierranortepadel.es`)
  * **Puesto:** Responsable de Administración y Facturación.
  * **Tipo de Usuario:** Interno.
  * **Privilegios:** Acceso de administrador al módulo de Facturación/Contabilidad y usuario de consulta en Ventas. Permite generar y cobrar facturas sin modificar los catálogos comerciales.

## 2. Grupo Personalizado Creado (Modo Desarrollador)
Para cubrir las necesidades específicas de la empresa, se ha creado un grupo propio desde el modo desarrollador:
* **Nombre del Grupo:** `Sierra Norte / Comercial Junior`
* **Grupo Heredado Base:** `Ventas / Usuario: solo mostrar documentos propios`
* **Derechos de Acceso sobre Modelos:**
  * `sale.order` (Pedidos de Venta): Lectura (Sí), Escritura (Sí), Creación (Sí), Eliminación (No).
  * `res.partner` (Contactos y Clientes): Lectura (Sí), Escritura (Sí), Creación (No), Eliminación (No).
* **Justificación:** Este grupo limita al comercial junior para que solo visualice y edite sus propios presupuestos y clientes asignados, impidiendo borrar registros críticos del sistema.

## 3. Demostración Práctica de Privilegios
Durante la grabación del vídeo explicativo se inicia sesión individualmente con cada usuario para contrastar sus limitaciones: se comprueba visualmente que el comercial no tiene acceso al menú de contabilidad y que el personal de administración no puede alterar los pedidos de venta.
