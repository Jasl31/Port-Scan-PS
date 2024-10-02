# Port-Scan-PS
Script basado en Powershell que contiene distintas herramientas que se usan para el escaneo de una red.

# Estructura del Menú
El script comienza mostrando un menú básico en pantalla, donde el usuario puede elegir una de las siguientes opciones:

Opción 1: Escanear toda la subred.
Opción 2: Escanear puertos en un equipo o dirección IP específica.
Opción 3: Escanear puertos en todos los equipos activos en la subred.

# Captura de la opción seleccionada
El script usa el comando Read-Host para capturar la entrada del usuario y asignarla a la variable $opcion. Luego, un bloque switch evalúa esta opción para decidir qué operación realizar.

# Escaneo de Puertos para Todos los Equipos Activos (Opción 3)
Obtención de la puerta de enlace predeterminada:

Usa el comando Get-NetRoute para obtener la puerta de enlace predeterminada de la red, que es la dirección de tu gateway. Esto es necesario para conocer el rango de IPs que se van a escanear.
Determinación del rango de la subred:

Se extrae el rango de la subred basada en la puerta de enlace. En este caso, parece que estás generando algo como 192.168.1. y posteriormente lo usarás para iterar sobre el resto de las direcciones IP en esa subred (rango de 1 a 254).
Escaneo de equipos activos:

Para cada dirección IP en el rango, se usa el comando Test-Connection para hacer un ping a cada IP dentro de la subred.
Si la IP responde al ping, el script muestra la IP con un mensaje verde, indicando que el host está activo.
Salida: Muestra todas las IP activas dentro del rango de la subred.

# Escaneo de Puertos para un Equipo o Dirección IP (Opción 2)
Conjunto de puertos a escanear:

La variable $porttoscan contiene una lista de puertos comunes que serán escaneados en el equipo o IP seleccionada. Estos incluyen puertos HTTP, HTTPS, SSH, RDP, entre otros.
Captura de la IP objetivo:

Se solicita al usuario que ingrese una dirección IP para escanear, y se almacena en la variable $direccion.
Iteración sobre los puertos:

El script intentará escanear los puertos especificados en la lista $porttoscan. Aquí falta agregar la lógica para el escaneo de puertos, que podrías implementar usando el módulo Test-NetConnection para probar si el puerto está abierto o cerrado.
