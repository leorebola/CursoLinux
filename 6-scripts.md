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

## Condicionales

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

## Bucles

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

```sh
Esta es la function1
Esta es la function2
```

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

```sh
Esta es la function1 con parámetro: param1
Esta es la function2 con parámetro: param2
```