# Configuracion de la misma llave SSH en otra computadora

Seguir los siguientes pasos para usar la misma llave ssh en otra computadora: 

# para linux

### En la Computadora A

1. **Montar la USB:**
   Inserta la USB y asegúrate de que esté montada. En la mayoría de los sistemas, se montará automáticamente.

2. **Copiar las llaves SSH a la USB:**
   Abre una terminal y copia las llaves SSH a la USB. Asumamos que la USB está montada en `/media/usb`:

   ```sh
   cp ~/.ssh/id_ed25519 /media/usb/
   cp ~/.ssh/id_ed25519.pub /media/usb/
   ```

3. **Desmontar la USB:**
   Desmonta la USB de forma segura:

   ```sh
   sudo umount /media/usb
   ```

### En la Computadora B

1. **Montar la USB:**
   Inserta la USB y asegúrate de que esté montada.

2. **Crear el directorio `.ssh` (si no existe):**
   Abre una terminal y crea el directorio `.ssh` en tu home si no existe:

   ```sh
   mkdir -p ~/.ssh
   ```

3. **Copiar las llaves SSH desde la USB:**
   Copia las llaves SSH desde la USB al directorio `~/.ssh`:

   ```sh
   cp /media/usb/id_ed25519 ~/.ssh/
   cp /media/usb/id_ed25519.pub ~/.ssh/
   ```

4. **Configurar permisos de las llaves:**
   Asegúrate de que los permisos de la llave privada sean correctos:

   ```sh
   chmod 600 ~/.ssh/id_ed25519
   chmod 644 ~/.ssh/id_ed25519.pub
   ```

5. **(Opcional) Configurar el archivo SSH `config`:**
   Si tienes múltiples llaves SSH, es útil configurar el archivo `~/.ssh/config` para especificar cuál usar para GitHub:

   1. Abre o crea el archivo `~/.ssh/config`:

      ```sh
      nano ~/.ssh/config
      ```

   2. Añade las siguientes líneas al archivo:

      ```sh
      Host github.com
        HostName github.com
        User git
        IdentityFile ~/.ssh/id_ed25519
      ```

   3. Guarda y cierra el archivo.

### Probar la configuración

Finalmente, prueba la conexión SSH a GitHub desde la Computadora B:

```sh
ssh -T git@github.com
```

Deberías ver un mensaje similar a:

```sh
Hi [tu_usuario]! You've successfully authenticated, but GitHub does not provide shell access.
```

Si ves este mensaje, significa que la configuración fue exitosa y ahora puedes usar la misma llave SSH en ambas computadoras para acceder a GitHub.


- --
# para windows

Sí, es posible usar la misma llave SSH en Windows. Aquí tienes los pasos detallados para hacerlo:

### En la Computadora A (Linux)

1. **Montar la USB:**
   Inserta la USB y asegúrate de que esté montada.

2. **Copiar las llaves SSH a la USB:**
   Abre una terminal y copia las llaves SSH a la USB. Supongamos que la USB está montada en `/media/usb`:

   ```sh
   cp ~/.ssh/id_ed25519 /media/usb/
   cp ~/.ssh/id_ed25519.pub /media/usb/
   ```

3. **Desmontar la USB:**
   Desmonta la USB de forma segura:

   ```sh
   sudo umount /media/usb
   ```

### En la Computadora B (Windows)

1. **Montar la USB:**
   Inserta la USB y asegúrate de que esté montada. Deberías poder ver la USB en el Explorador de Archivos.

2. **Instalar Git Bash:**
   Si aún no lo has hecho, instala Git para Windows, que incluye Git Bash, un entorno que proporciona una terminal similar a la de Linux. Puedes descargarlo desde [gitforwindows.org](https://gitforwindows.org/).

3. **Crear el directorio `.ssh` (si no existe):**
   Abre Git Bash y crea el directorio `.ssh` en tu directorio de usuario (si no existe):

   ```sh
   mkdir -p ~/.ssh
   ```

4. **Copiar las llaves SSH desde la USB:**
   Copia las llaves SSH desde la USB al directorio `~/.ssh`. Supongamos que la USB está montada como `D:`:

   ```sh
   cp /d/id_ed25519 ~/.ssh/
   cp /d/id_ed25519.pub ~/.ssh/
   ```

5. **Configurar permisos de las llaves:**
   Asegúrate de que los permisos de la llave privada sean correctos. En Git Bash, ejecuta:

   ```sh
   chmod 600 ~/.ssh/id_ed25519
   chmod 644 ~/.ssh/id_ed25519.pub
   ```

6. **(Opcional) Configurar el archivo SSH `config`:**
   Si tienes múltiples llaves SSH, es útil configurar el archivo `~/.ssh/config` para especificar cuál usar para GitHub:

   1. Abre Git Bash y edita o crea el archivo `~/.ssh/config`:

      ```sh
      nano ~/.ssh/config
      ```

   2. Añade las siguientes líneas al archivo:

      ```sh
      Host github.com
        HostName github.com
        User git
        IdentityFile ~/.ssh/id_ed25519
      ```

   3. Guarda y cierra el archivo.

### Probar la configuración

Finalmente, prueba la conexión SSH a GitHub desde Git Bash en Windows:

```sh
ssh -T git@github.com
```

Deberías ver un mensaje similar a:

```sh
Hi [tu_usuario]! You've successfully authenticated, but GitHub does not provide shell access.
```

Si ves este mensaje, significa que la configuración fue exitosa y ahora puedes usar la misma llave SSH en Windows para acceder a GitHub.


- --
<br>

## De ultimo configurar usuario


Ejecuta

  git config --global user.email "you@example.com"
  git config --global user.name "Tu Nombre"


