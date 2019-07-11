# 6. SCRIPTS

## Que es un shell script

```sh
#!/bin/bash

# Ejemplo de shell script.

echo "El directorio actual es:"
pwd

echo "El directorio de este usuario es: $HOME"

echo "Contiene los siguientes archivos y directorios:"
ls -la

# Sustitución de comando
echo "En total son" $(ls -la | wc -l) "archivos"

echo `date` " - fin de ejecución" >> mi-script.log
```

## Ejecutar un shell script

```console
$ chmod +x my-script.sh

$ sh my-script.sh

# o:

$ ./my-script.sh
```

## Variables

```sh
nombre="Juan Perez"
edad=30

# No debe colocar espacios en el operador de asignacion: =

echo $nombre
echo $edad

echo "$nombre"
echo "$edad"

echo "Su nombre es: $nombre"
echo "Su edad es: $edad"

echo "Su nombre es:" $nombre
echo "Su edad es:" $edad
```

Salida:
```sh
Juan Perez
30
Juan Perez
30
Su nombre es: Juan Perez
Su edad es: 30
Su nombre es: Juan Perez
Su edad es: 30
```

## Comparación

### Comparaciones de cadenas alfanuméricas

```console
Operador		Verdad (TRUE) si:
------------------------------------------
cadena1 = cadena2	cadena1 es igual a cadena2
cadena1 != cadena2	cadena1 no es igual a cadena2
cadena1 < cadena2	cadena1 es menor que cadena2
cadena1 > cadena 2	cadena1 es mayor que cadena 2
-n cadena1		cadena1 no es igual al valor nulo (longitud mayorque 0)
-z cadena1		cadena1 tiene un valor nulo (longitud 0)
```

### Comparación de valores numéricos

```console
Operador		Verdad (TRUE) si:
------------------------------------------
x -lt y			x menor que y
x -le y			x menor o igual que y
x -eq y			x igual que y
x -ge y			x mayor o igual que y
x -gt y			x mayor que y
x -ne y			x no igual que y
```

### Comprobación de atributos de fichero

```console
Operador		Verdad (TRUE) si:
------------------------------------------
-d fichero		fichero existe y es un directorio
-e fichero		fichero existe
-f fichero		fichero existe y es un fichero regular (no un
			directorio, u otro tipo de fichero especial)

-r fichero		Tienes permiso de lectura en fichero
-s fichero		fichero existe y no esta vacio
-w fichero		Tienes permiso de escritura en fichero
-x fichero		Tienes permiso de ejecucion en fichero (o de busqueda
			si es un directorio)

-O fichero		Eres el dueño del fichero
-G fichero		El grupo del fichero es igual al tuyo.

fichero1 -nt fichero2	fichero1 es mas reciente que fichero2
fichero1 -ot fichero2	fichero1 es mas antiguo que fichero2
```

## Condicionales y Bucles

### if

```sh
if [[ $num = 1 ]]
then
    echo 'El número es uno.'
fi
```

```sh
if [[ $num = 1 ]]
then
    echo 'El número es UNO.'
else
    echo 'El número es DISTINTO A UNO.'
fi
```

```sh
if [[ $num = 1 ]]
then
    echo 'El número es UNO.'
elif [[ $num = 2 ]]
    echo 'El número es DOS.'
else
    echo "El número no es UNO ni DOS." 
fi
```

```sh
DIRECTORIO=$1

# Chequear existencia de directorio
if [ -d $DIRECTORIO ]
then
    echo "El directorio \"$DIRECTORIO\" existe."
else
    echo "El directorio \"$DIRECTORIO\" no existe y será creado."
    mkdir $DIRECTORIO
fi
```

### for

```sh
for file in *.log; do
    echo "El archivo $file tiene un tamaño de" $(du -sh $file | cut -f1)
done
```

```sh
for (( counter=0; counter<10; counter++ ))
do
    echo "$counter"
done
```

### while

```sh
i=0

while [[ $i -lt 5 ]]
do
     echo "Iteración $i ejecutada."

     let i=$i+1
done
```

### case

```sh
NUM=$1

if [[ $NUM -le 0 || $NUM -ge 10 ]]
then
    echo "El número ingresado es incorrecto."
    exit 1
fi

case $NUM in
    0)
        echo "El número ingresado es cero"
        ;;
    1)
        echo "El número ingresado es uno"
        ;;
    2)
        echo "El número ingresado es dos"
        ;;
    3)
        echo "El número ingresado es tres"
        ;;
    *)
        echo "El número ingresado es mayor a 3 y menor a 10"
        ;;
esac
```

## Pasar parámetros

```sh
$ sh myprograma.sh "sum" 10 5
```

```sh
if [[ $# = 3 ]]
then
    if [[ $1 = "sum" ]]
    then
        echo "El resultado de la suma es: " $(( $2 + $3 ))
    else
        echo "Operación no soportada"
    fi
else
    echo "Número de parámetros incorrectos"
fi
```

```sh
while [[ -n $1 ]]
do
        echo "$1"
        shift
done
```

```sh
# file:test-parameters.sh

echo 'Resultado de $#:' $#
echo 'Resultado de $@:' $@
echo 'Resultado de $?:' $?
```

Salida:
```console
$ test-parameters.sh "Hola" 123 "Linux"

Resultado de $#: 3
Resultado de $@: Hola 123 Linux
Resultado de $?: 0
```

Códigos de salida: $?

### Ejemplo:

```sh
# file:test-code.sh

touch /root/myfile.txt
echo "Archivo creado!"
```

```console
$ sh test-code.sh
touch: cannot touch ‘/root/myfile.txt’: Permission denied
Archivo creado!
```

```sh
# file:test-code.sh

touch /root/myfile.txt 2> /dev/null

if [ $? -eq 0 ]
then
  echo "Archivo creado exitosamente."
  exit 0
else
  echo "No se pudo crear el archivo." >&2
  exit 1
fi
```

Ejecución:
```console
$ test-code.sh
No se pudo crear el archivo.
$ echo $?
1
```

### Interactivo:

```sh
echo -n "Ingrese un numero: "
read VAR

if [[ $VAR -gt 10 ]]
then
    echo "El número ingresado es mayor a 10."
else
    echo "El número ingresado es menor a 10."
fi
```



## Funciones

Declarar una función:

```sh
function function1
{
    echo "Esta es la function1"
}

function2()
{
    echo "Esta es la function2"
}

function1
function2
```

Salida:

```sh
Esta es la function1
Esta es la function2
```

Funciones con parámetros:

```sh
function function1
{
    echo "Esta es la function1 con parámetro: $1"
}

function2()
{
    echo "Esta es la function2 con parámetro: $1"
}

function1 "param1"
function2 "param2"
```

Salida:

```sh
Esta es la function1 con parámetro: param1
Esta es la function2 con parámetro: param2
```