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

## Unir ficheros ##

- paste
- join

## Manipulación de cadenas de texto ##

- extraer
- borrar
- reemplazar

