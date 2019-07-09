# 5. PROCESAMIENTO DE FICHEROS DE TEXTO #

![](images/5/nano.png)

## Impresión de ficheros ##

- cat
- head
- tail

### cat

```console
$ cat filename
```

```console
$ cat filename1 filename2
```

```console
# Parametros útiles:

-n: Numera todas las líneas de salida.

-b: Número de líneas de salida no vacías.
```

Copiar contenido a otro archivo:

```console
$ cat filename > filename-new
```

```console
$ cat filename >> filename-new
```

```console
$ cat filename1 filename2 > filename-new
```

### head

```console
$ head filename
```
```console
$ head -5 filename
```
```console
$ head -c5 filename
```

### tail

```console
$ tail filename
```

```console
$ tail -5 filename
```

```console
$ tail -f filename
```

```console
# Parametros útiles:

-n: muestra las últimas n líneas del archivo.

-f: muestra las últimas líneas de un archivo en tiempo real.
```

## Navegación de ficheros ##

- less

| ![](images/5/less-command-examples-linux-featured.png) | 
|:--:| 
| *Image from: https://linuxhandbook.com/wp-content/uploads/2018/08/less-command-examples-linux-featured.png* |

```console
$ less filename
```

Argumentos útiles:

```console
$ less -N filename

# Mostrar número de cada línea
```

```console
$ less -p BUSCAR_ALGO filename
```

```console
$ less +n filename

# Muestra el archivo desde la linea n
```

```console
$ less -M filename

# Muestra información: cantidad de lineas, % de avance
```

```console
$ file * | less

# Para inspeccionar directorios con muchos archivos
```

```console
$ less -S filename

# Deshabilitar auto-ajuste de líneas
```

```console
$ less +F filename

# Idem a: tail -f filename
```

Comandos:
```console
Navegación:

- Teclas de Flechas/AvPag/RePag/Inicio/Fin: .
- g: Ir al final del texto. 
- G: Ir al inicio del texto. 
- Ng: Saltar a línea número N.

Búsqueda:

- /: Ingresar una palabra a ser buscada avanzando dentro del texto. Se pueden utilizar expresiones regulares.
- ?: Ingresar una palabra a ser buscada retrocediendo dentro del texto. Se pueden utilizar expresiones regulares.
- n: Ir a siguiente coincidencia (después de una búsqueda).
- N: Ir a coincidencia anterior (después de una búsqueda).

- q: salir
```

## Edición de ficheros ##

- wc
- grep
- cut
- sed
- sort
- uniq
- shuf


### wc (word count) 

Parámetros:

```console
$ wc -l filename

# número de lineas 
```

```console
$ wc -m filename

# imprime el número de caracteres
```

```console
$ wc -L filename

# imprime la longitud de la línea más larga
```

```console
$ wc -w filename

# imprime el número de palabras
```

Ejemplos:

```console
$ wc -l *.txt

  240 countries.txt
  104 iso_8859-1.txt
    8 linux.txt
    3 users.txt
  355 total
```

```console
$ cat /etc/passwd | grep /home | wc -l 
   3
```

```console
$ ls | wc -l
```

### grep (Global Regular Expression Print)

```console
$ grep option search_pattern filename
```

Parámetros y formas de usar:

```console
$ grep PALABRA filename
```

```console
$ grep PALABRA *.txt
```

```console
$ grep PALABRA *.txt > resultados.txt
```

```console
$ grep -i PALABRA *.txt

# case insensitive
```

```console
$ grep -r PALABRA /home/user1/
```

```console
$ grep -n PALABRA *.txt

# mostrar el número de línea en el que coincide el patrón
```

```console
$ grep -color PALABRA *.txt
```

```console
Otros parámetros:

-E nos permite usar expresiones regulares. Equivalente a usar egrep.
-H nos imprime el nombre del archivo con cada coincidencia.
```

### cut

```console

```

```console

```

### sed

```console

```

```console

```

### sort

```console

```

```console

```

### uniq

```console

```

```console

```

### shuf

```console

```

```console

```

## Unir ficheros ##

- paste
- join

## Manipulación de cadenas de texto ##

- extraer
- borrar
- reemplazar

