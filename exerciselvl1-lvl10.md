---
title: 'Practica Overthewhire'
description: 'Aprendiendo Linux'
pubDate: 'February 18 2024'
---

# Overtherire and Bandit
Use Command<br>
<code>ls</code> list directory contents. <br>
<code>cd</code> change the working directory.<br>
<code>cat</code> concatenate files and print on the standard output.<br>
<code>file</code> determine file type.<br>
<code>du</code> estimate file space usage.<br>
<code>find</code> search for files in a directory hierarchy.<br>
<code>sort</code> sort lines of text files.<br>
<code>uniq</code> report or omit repeated lines
.<br>

## Bandit level 0
* bandit0@bandit.labs.overthewire.org -p 2220 passwd: bandit0
  Use: ssh
* flag: NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL

## Bandit level 1
* bandit1@bandit.labs.overthewire.org -p 2220 passwd: bandit0<br>
  __Command Use:__ ls, cd cat, file, du find
* __flag:__ rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi  

__whoami:__ usuario actual.
  hostname -I: muestra la dirección ip del hostname actual. 

__Command Use:__<br>
<code>cat ./</cde>: en muestra en el directorio actual.<br>
<code>cd /home/bandit1/-</code>: uso de la ruta absoluta.<br>
<code>cat ./* </code>: muestra todo lo que hay en el directorio actual.<br>
<code>cat ./home/bandit1/*</code>: muestra todo con ruta absoluta.<br>
<code>cat $(pwd)/-</code>: <br>
<code>cat $(pwd)/*-</code>: <br>
<code>cat ${pwd}./-</code>: <br>
<code>cat ${pwd}./*</code>: <br>

## Bandit level 2
* bandit2@bandit.labs.overthewire.org -p 2220 passwd: bandit0<br>
* __Use:__ ls, cd cat, file, du find
* __flag:__ aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG

__Command Use:__<br>
<code>cat "name of data"</code>: entre comillas cuando se tiene espacios.<br>
<code>cat spaces\ in\ this\ filename</code>: cuando empezamos a escribir usamos la tecla tab para autocomplete. uso de la tecla tab.<br>
<code>cat sp*</code>: uso del asterisco para decir que me muestre todo lo empieza con sp.<br>
<code>cat *ame</code>:<br>
<code>cat *this*</code>:<br>

## Bandit level 3
* bandit3@bandit.labs.overthewire.org -p 2220 passwd: bandit0<br>
__Use:__ ls, cd cat, file, du find
* __Flag:__ 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
  
__Command use:__<br>
  <code>cat inhre/.*</code>:<br>
  <code>find . -type f -printf "%f\t%p\t%u\t%g\t%m\n" | column -t</code>:<br>
  <code>find . -name .hidden | xargs cat</code>:
  <code></code>

## Bandit level 4
__Descripción:__ La contraseña para el siguiente nivel se almacena en el único archivo legible por humanos en el directorio inhere.
* bandit4@bandit.labs.overthewire.org -p 2220 <br>
* __Command Use:__<br>
<code>file inhere/*</code>:<br>
<code>find -name -file07 | xargs cat</code>:<br>
<code>cat $(find . -name -file07)</code>:<br>
<code>cat inhere/-file07</code>:<br>
* flag: lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
  
## Bandit level 5
__Description:__ La contraseña para el siguiente nivel se almacena en un archivo en algún lugar del directorio interno y tiene todas las siguientes propiedades: 
* legible por humanos 
* 1033 bytes de tamaño 
* no ejecutable<br> 
* ssh bandit5@bandit.labs.overthewire.org -p 2220<br>

__Command Use:__<br>
<code>find -size 1033c | xargs cat | xargs</code> búsqueda por el size.<br>
<code>find . -type f -readable ! -executable -size 1033c</code> Búsqueda si es de lectura, ejecutable y por su size.<br>
<code>find . -type f -readable ! -executable -size 1033c | xargs cat | xargs</code><br>
__Flag:__ P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU

## Bandit level 6
__Description:__
La contraseña para el siguiente nivel se almacena en algún lugar del servidor y tiene todas las propiedades siguientes:
* propiedad del usuario bandit7 
* propiedad del grupo bandit6 
* 33 bytes de tamaño
* ssh bandit6@bandit.labs.overthewire.org -p 2220<br>

__Command Use:__<br>
<code>find / -user bandit7 -group bandit6 -size 33c 2>/dev/null | xargs cat</code><br>
<code></code><br>

__Flag:__ z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S

## Bandit level 7
__Description:__
La contraseña para el siguiente nivel se almacena en el archivo data.txt junto a la palabra millonésima.<br>

__Commands necesarios para este nivel__<br>
man, grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd<br>

__Command Use:__<br>
<code>cat data.txt | wc -l</code> Cuentame todas las lineas que tiene data.<br>
<code>cat data.txt | wc -c</code> Cuenta cuantas caracteres hay en este archivo<br>
<code>grep "millionth" data.txt</code> <br>
<code>grep '/millionth/ data.txt'</code> <br>
<code>grep '/millionth/ data.txt' -n</code> <br>
<code>awk '/millionth/ data.txt'</code><br>
<code>awl '/millionth/' data.txt | awk '{print $2}'</code> <br>
<code>awl '/millionth/' data.txt | awk 'NF{print $NF}'</code> <br>
<code>awl 'NR==10032' </code> <br>

__Flag:__ TESKZC0XvTetK0S9xNwm25STk5iWrBvP

## Bandit level 8
__Description:__
La contraseña para el siguiente nivel se almacena en el archivo data.txt y es la única línea de texto que aparece solo una vez.

__Command Use:__<br>
<code>cat data.txt | sort | uniq -u</code> <br>
<code> </code> <br>

__Flag:__ EN632PlfYiZbn3PhVK3XOGSlNInNE00t

## Bandit level 9
__Description:__
La contraseña para el siguiente nivel se almacena en el archivo data.txt en una de las pocas cadenas legibles por humanos, precedida por varios caracteres "=".

__Command Use:__<br>
<code>contador=1; strings data.txt | grep "===" | while read line; do echo "Linea $contador: $line"; let contador+=1; done | awk 'NR==4'</code>,br

<code>contador=1; strings data.txt | grep "===" | while read line; do echo "Linea $contador: $line"; let contador+=1; done | awk 'NR==4' | awk "NF{print $NF}"</code>

__Flag:__ G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s

## Bandit level 10
__Description:__
La contraseña para el siguiente nivel se almacena en el archivo data.txt, que contiene datos codificados en base64.

__Command Use:__<br>
<code>base64 -d data.txt</code><br> 
<code>cat data.txt | base64 -d | tr '' '\n}'</code><br>

__Flag:__ 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM:
