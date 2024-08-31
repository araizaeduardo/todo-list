# todo-list (Versión 1)

> Este proyecto es una aplicación de lista de tareas (todo-list) que utiliza almacenamiento local del navegador (localStorage) para guardar las tareas del usuario.

## Instalación con Nginx

1. Clona el repositorio:
   ```
   git clone https://github.com/tu-usuario/todo-list.git
   cd todo-list
   ```

2. Convierte el archivo HTML a index.html y muévelo a /var/www/html:
   ```
   mv todo-list-bootstrap.html index.html
   sudo mv index.html /var/www/html/
   ```

3. Cambia los permisos del archivo para que pertenezca al usuario www-data:
   ```
   sudo chown www-data:www-data /var/www/html/index.html
   sudo chmod 644 /var/www/html/index.html
   ```

4. Asegúrate de que el directorio /var/www/html tenga los permisos correctos:
   ```
   sudo chown www-data:www-data /var/www/html
   sudo chmod 755 /var/www/html
   ```

5. Configura Nginx:
   ```nginx
   server {
       listen 80;
       server_name tu-dominio.com;
       root /var/www/html;
       index index.html;
       
       location / {
           try_files $uri $uri/ /index.html;
       }
   }
   ```

6. Reinicia Nginx:
   ```
   sudo systemctl restart nginx
   ```

7. Accede a la aplicación en tu navegador: `http://tu-dominio.com`

## Instalación con Docker

1. Clona el repositorio:
   ```
   git clone https://github.com/tu-usuario/todo-list.git
   cd todo-list
   ```

2. Construye la imagen de Docker:
   ```
   docker build -t todo-list .
   ```

3. Ejecuta el contenedor:
   ```
   docker run -d -p 80:80 todo-list
   ```

4. Accede a la aplicación en tu navegador: `http://localhost`

Nota: Asegúrate de tener Docker instalado en tu sistema antes de seguir estos pasos.
