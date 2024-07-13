---
title: 'Practica Overthewhire'
description: 'Aprendiendo Linux'
pubDate: 'February 18 2024'
---

## Bandit level 11
__Description:__
La contraseña para el siguiente nivel se almacena en el archivo data.txt, donde todas las letras minúsculas (a-z) y mayúsculas (A-Z) se han rotado 13 posiciones.

__Command Use:__<br>
<code>cat data.txt | tr '[G-ZA-Fg-za-f]' '[T-ZA-St-za-s]'</code>
<code>cat data.txt | tr '[G-ZA-Fg-za-f]' '[T-ZA-St-za-s]' | awk "NF{print $NF}"</code>

__Flag:__ JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv

## Bandit level 12
__Description:__
La contraseña para el siguiente nivel esta almacenada en un data.txt, que es hexdump de un archivo de ha sido comprimido repetidamente.
Para este nivel puede ser util crea un directorio bajo /tmp en el que pueda trabajar. Utilice mkdir con un nombre dificil de adivinar del directorio.

__Command Use:__<br>
<code>copy data.hex  </code>

<code>xxd -r data.hex > data</code>

<code>file data </code>

<code>mv data data.gzip</code><br>

Se realiza un bashscrip para descomprimir vairas veces con un bucle for y haciendo uso de 7z, grp, tail, awk.

```bash
 
#!/bin/bash
 
 name_decompressed=$(7z l content.gzip | grep "Name" -A 2 | tail -n 1 | awk 'NF{print $NF}')
 7z x content.gzip >/dev/null 2>&1
 
 while true; do
     7z l $name_decompressed >/dev/null 2>&1
 
     if [ "$(echo $?)" == "0" ]; then
         decompressed_next=$(7z l $name_decompressed | grep "Name" -A 2 | tail -n 1 | awk 'NF{print $NF}')
         7z x $name_decompressed >/dev/null 2>&1 && name_decompressed=$decompressed_next
     else
         cat $name_decompressed
         rm data* 2>/dev/null
         exit 1
     fi
 done
```

__Flag:__ The password is: wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw 

## Bandit level 13
__Description:__
La contraseña para el siguiente nivel esta almacenado en /etc/bandit_pass/bandit14 y solo puede ser leido por el usuario bandit14. Para este nivel tu no necesitas la contraseña, pero tu obtienes la clave ssh y utilizar para el siguiente nivel.
Nota: localhost is a nombre del anfitrion hace referencia a la maquina que tu estas trabajando.

__Command Use:__<br>
<code>ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220</code>
<code>cd /etc/bandit_pass && cat bandit14 </code>

__flag:__ fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq

## Bandit level 14
__Description:__
La contraseña para el siguiente nivel se puede recuperar enviando la contraseña del nivel actual al puerto 30000 en localhost.\

__Command Use:__<br>
<code>  </code>