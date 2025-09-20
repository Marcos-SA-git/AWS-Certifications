# Introducción

En este archivo encontrarás varios tips, consejos y/o sugerencias que tal vez te ayuden a maximizar tu experiencia de estudio, te aporten conocimientos útiles para situaciones reales o que puedan caer en el examen, o incluso que aprendas contenido extra que no encontrarás en otras lecciones tanto oficiales como de terceros.

A continuación hay un índice con todos los tips. No siguen ningún orden en concreto y es únicamente para facilitar la navegación.

---

## Índice

[Usar AWS CLI en una terminal Linux desde un equipo Windows con WSL](#usar-aws-cli-en-una-terminal-linux-desde-un-equipo-windows-con-wsl)

---

## Usar AWS CLI en una terminal Linux desde un equipo Windows con WSL

En este tip veremos cómo usar la consola de Linux en Windows sin tener que recurrir a máquinas virtuales como VirtualBox para poder usar la consola de comandos de AWS (CLI).

1. **Abre el menú de características:**
   - Puedes acceder al menú de características rápidamente si en el buscador de Windows 10 u 11 pones "`caract`". Te debería salir la primera o segunda opción (una opción común es el programa "Mapa de caracteres").
   - Si no te aparece en el buscador, puedes ir desde la interfaz moderna de Windows en `Configuración -> Sistema -> Características opcionales -> Más características de Windows`.
   - Si eres más de la "old school" puedes usar el buscador de Windows poniendo "`pan`" y accediendo así al `Panel de Control -> Programas y Características -> Activar o desactivar características de Windows`. (Ubicado en el lateral superior izquierdo).

   Sea cual sea el camino que escojas te debería aparecer la siguiente ventana, en la cual deberás bajar y marcar la opción "`Subsistema de Windows para Linux`", también conocido como WSL (*Windows Subsystem for Linux*):

   ![Ventana de características opcionales en Windows mostrando la opción de habilitar WSL](/AWS-Certifications/SAA-C03/assets/windows-characteristics.png)

2. **Instala Ubuntu:**
   Tras esto, reinicia Windows, y cuando terminen de instalarse las nuevas características, ve a la tienda de Microsoft y busca "`Ubuntu`" e instálalo.

3. **Configura Ubuntu:**
   En cuanto termine la instalación, abre la aplicación y verás que aparecen 2 terminales. En una de ellas, tras terminar de instalarse unas cosas, te preguntará por un usuario y una contraseña. Los completas con lo que quieras y tras finalizar la configuración, cierras las terminales.

4. **Abre Ubuntu y actualízalo:**
   Tras la instalación, conviene primero actualizar el sistema con los siguientes comandos:

   ```shell
   # Actualiza la lista de paquetes disponibles y versiones más recientes.
   sudo apt update
   # Instala las actualizaciones disponibles de todos esos paquetes.
   sudo apt upgrade
   ```

5. **Instala AWS CLI:**
   Una vez acabe de actualizar, ya tienes casi todo listo para seguir las [instrucciones oficiales de la instalación de AWS CLI](https://docs.aws.amazon.com/es_es/cli/latest/userguide/getting-started-install.html) como hemos visto en las prácticas.

   Podrás notar que la documentación se utiliza el programa "`unzip`" para descomprimir el archivo con el instalador del CLI. Este no viene instalado por defecto, por lo que puedes instalarlo con el comando `sudo apt install unzip`. Te preguntará si estás seguro de querer instalar el programa, a lo que le decimos que sí (`y`) y cuando termine podemos instalar AWS CLI como en la documentación con los siguientes comandos:

   ```shell
   curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
   unzip awscliv2.zip
   sudo ./aws/install
   ```

6. **Comprueba la instalación:**
   Puedes comprobar que funciona correctamente comprobando la versión instalada con la siguiente instrucción:

   ```shell
   aws --version
   # Debería devolver algo como:
   # aws-cli/2.30.6 Python/3.13.7 Linux/6.6.87.2-microsoft-standard-WSL2 exe/x86_64.ubuntu.24
   ```

7. **BONUS:**
   Dado que ahora la terminal de Ubuntu está integrada en Windows, puedes ejecutarla desde el famoso editor de código Visual Studio Code!
   Tan solo abre el menú de terminal, y entre las opciones disponibles aparecerá Ubuntu! Junto con extensiones como las de GitHub te permitirán trabajar con el código y guardar tus scripts directamente en tu repositorio sin tener 2 o más ventanas desperdigadas por la pantalla.

   *Happy Coding!*

---

