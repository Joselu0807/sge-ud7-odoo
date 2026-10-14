# Registro de errores y resolución durante la instalación

Durante la puesta en marcha de Odoo 17 para **Sierra Norte Padel Pro S.L.** en mi ordenador, me equivoqué un par de veces al copiar comandos y al configurar la base de datos. Aquí detallo los pequeños fallos que tuve y cómo los arreglé sobre la marcha.

## Comprobaciones previas
Antes de levantar el entorno con Docker, comprobé que el servicio de Docker Desktop estaba en verde y miré en el administrador de tareas que no hubiera ningún proceso raro bloqueando los puertos.

## Tabla de errores y soluciones

| Qué error me salió / Qué pasó | Por qué fue el fallo | Cómo lo solucioné | Dónde lo miré |
| :--- | :--- | :--- | :--- |
| **`yaml: line 9: mapping values are not allowed in this context`** al ejecutar el comando para arrancar. | Me equivoqué al tabular con la barra espaciadora en una línea del archivo `docker-compose.yml`, ya que YAML es súper estricto con los espacios y las tabulaciones. | Abrí el archivo en Visual Studio Code, borré la tabulación de esa línea y puse exactamente dos espacios con el teclado. Volví a lanzar el comando y arrancó a la primera. | Busqué el mensaje del error en Google y vi que era un problema típico de indentación en YAML. |
| **Odoo me dio un error de conexión con la base de datos** justo después de crearla en el navegador. | Le di demasiado prisa a hacer clic en el navegador nada más escribir `docker compose up -d`, y el contenedor de PostgreSQL aún se estaba encendiendo por dentro. | Esperé medio minuto a que terminara de arrancar del todo el contenedor de la base de datos y actualicé la página web. Con eso ya me dejó entrar sin problema. | Experiencia de prácticas anteriores con contenedores que tardan unos segundos en inicializarse. |
| **Me equivoqué al poner el correo y la contraseña** al crear la base de datos por primera vez y no podía entrar. | Había guardado mal las credenciales iniciales en el formulario de Odoo al registrar la BD limpia. | Borré la base de datos defectuosa desde el panel de gestión de Odoo (`localhost:8069/web/database/manager`) usando la *Master Password*, volví a crear la base de datos `padelpro_db` desde cero bien escrita y listo. | Documentación básica de administración de bases de datos en Odoo. |