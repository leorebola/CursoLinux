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

### if

```sh
if [[ $num = 1 ]];
then
    echo 'El número es uno.'
fi
```

```sh
if [[ $num = 1 ]];
then
    echo 'El número es UNO.'
else
    echo 'El número es DISTINTO A UNO.'
fi
```

```sh
if [[ $num = 1 ]];
then
    echo 'El número es UNO.'
elif [[ $num = 2 ]]
    echo 'El número es DOS.'
else
    echo "El número no es UNO ni DOS." 
fi
```

```console
[] vs [[]]

Corchetes simples: Para comparaciones ==, !=, <, y > debe utilizarse eq, ne,lt y gt respectivamente.

Corchetes dobles: Para comparaciones puede usarse: ==, !=, <, y >.

Otros:

if [ x ] && [ y ]; then

vs.

if [[ x  &&  y ]]; then
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
#while [ $i -lt $max ]
while [[ $i < 5 ]]
do
     echo "Iteración $i ejecutada."

     let i=$i+1
     # i=$(( $i + 1 ))
done
```


## Pasar parámetros

```sh
$ sh myprograma "sum" 10 5
```

```sh
if [[ $# == 3 ]];
then
    if [[ $1 == "sum" ]];
    then
        echo "El resultado de la suma es: " $(( $2 + $3 ))
    else
        echo "Operación no soportada"
    fi
else
    echo "Número de parámetros incorrectos"
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