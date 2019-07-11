# Ejercicios

1. Realizar un script llamado "01­hola­mundo.sh" que muestre por pantalla "Hola mundo!"

2. Realizar un script llamado "02­hola­mundo.sh" que reciba por parámetro el nombre de una persona e imprima por pantalla "Hola nombre_persona!". Además debe validar que se ingrese un solo argumento, en otro caso devolver un mensaje de error y código de salida 1.

3. Realizar un script llamado "03logger.sh" que cree un directorio llamado "files" (si ya no existe) y dentro de él, generar un archivo llamado salida.log con la siguiente información:

```txt
fecha y hora - Inicio del proceso.
Ejecución número: 1
Ejecución número: 2
Ejecución número: 3
Ejecución número: 4
Ejecución número: 5
```
- *Además, cada vez que se ejecute el script, no debe borrar los datos anteriores.
Ayuda: Usar el comando "date" y un bucle.*

4. Realizar un script llamado "04checkuser.sh" que imprima por pantalla "TRUE" si el nombre de usuario que le indicamos por parámetro existe en el archivo /etc/passwd. Deberá retornar "FALSE" si no existe.

5. Realizar un script llamado "05math.sh" que haga sumas y restas de números enteros. Se deberán declarar dos funciones: suma() y otra resta(). Además utilizar "case" para capturar las opciones "SUMA" o "RESTA". El script retornará por pantalla: "El resultado de la suma es: " o "El resultado de la resta es: ".

6. Realizar un script "06users.sh" que retorne toda la lista de usuarios que figuran en /etc/passwd. Solo los nombres de usuarios y ordenados alfabéticamente.