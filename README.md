# Configuración de VPS

Este proyecto configura mi VPS desde cero en caso de reinstalarla.

Hay que seguir los siguientes pasos:

## Antes de Reinstalar la VPS

* Copiar los directorios importantes del directorio personal del usuario debian (usuario por defecto de la VPS)
* Borrar las anteriores claves de google-authenticator

## Tras reinstalar la VPS

* Esperar el correo de OVH y acceder con la contraseña al servidor por el puerto 22.
* Inmediatamente se acceda, cambiar la contraseña del usuario debian.
* Instalar Ansible para ejecutar el playbook adjunto
* Hacer una copia de este proyecto al directorio personal del VPS.
* Moverse al siguiente directorio y ejecutar el playbook de Ansible, hará la siguiente configuración:
    * Actualizar el sistema operativo.
    * Instalar el libpam-google-authenticator para configuración personal más adelante.
    * Configurar el servidor ssh a partir de los ficheros con nombre sshd en el directorio config.
    * Instalar fail2ban y configurarlo correctamente a partir del archivo jail.local del directorio config.
    * Instalar Docker y Docker Compose.
    * Levantar los contenedores de los directorios stack que hay en el directorio config (Nginx Proxy Manager, Portainer, Netdata, Wazuh y Jellyfin).
* Hacer el google-authenticator.
* Copiar el resto de directorios.
* Hacer las configuraciones de todos los servicios en los contenedores.
## Listo
Una vez cumplidos estos pasos, el acceso ssh a la VPS estará por un puerto diferente al 22 con 2FA activo y el fail2ban corriendo correctamente. También estarán levantados varios microservicios de Docker.