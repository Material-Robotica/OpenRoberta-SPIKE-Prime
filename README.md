# Open Roberta + LEGO SPIKE Prime (Pybricks)
 
Guía para programar el **LEGO SPIKE Prime** desde el [Open Roberta Lab](https://lab.open-roberta.org) con **Windows 11**, usando el firmware **Pybricks** y la conexión **Bluetooth del navegador**.
 
## Guía paso a paso
 
👉 **[Abrir la guía Open Roberta + SPIKE Prime](https://material-robotica.github.io/OpenRoberta-SPIKE-Prime/Guia-OpenRoberta-SPIKE.html)**
 
> Guía hermana para LEGO EV3 con leJOS: [Open Roberta + EV3](https://material-robotica.github.io/openRoberta-ev3/Guia-OpenRoberta-EV3.html)
 
---
 
## Qué se necesita
 
- Navegador **Google Chrome** o **Microsoft Edge** (Firefox y Safari no tienen Bluetooth web).
- PC con **Bluetooth** (en PC de escritorio sin Bluetooth: adaptador Bluetooth USB).
- Cable **USB** del SPIKE Prime, solo para instalar el firmware.
No hace falta instalar programas, Java ni drivers en la PC: todo funciona desde el navegador.
 
## Resumen
 
| | SPIKE Prime (Pybricks) |
|---|---|
| Sistema en el robot | Firmware **Pybricks** instalado en el hub |
| Programa puente | Ninguno: conexión directa desde el navegador |
| Conexión | **Bluetooth** del navegador |
| Lenguaje generado | Python (MicroPython) |
| Tarjeta en el Lab | **Spike Prime / Robot Inventor / Pybricks** |
 
## Pasos
 
**Una sola vez por hub** ([Parte A de la guía](https://eliizquierdo.github.io/openRoberta-spike/Guia-OpenRoberta-SPIKE.html)):
 
1. Actualizar el hub con la app oficial de LEGO SPIKE si hace mucho que no se usa.
2. Instalar Pybricks desde [code.pybricks.com](https://code.pybricks.com) → configuración → **Install Pybricks Firmware**.
3. Verificar que el hub **no** esté emparejado en *Configuración → Bluetooth y dispositivos* de Windows (si aparece, **Quitar**).
4. Probar el hub con el programa de prueba de Python (abajo).
**En cada clase** ([Parte B de la guía](https://eliizquierdo.github.io/openRoberta-spike/Guia-OpenRoberta-SPIKE.html)):
 
1. Activar el Bluetooth de Windows y cerrar cualquier pestaña de code.pybricks.com.
2. En el Lab elegir **Spike Prime / Robot Inventor / Pybricks**.
3. Armar el programa y tocar **▶** → elegir el hub → **Emparejar**.
## Programa de prueba (Pybricks, Python)
 
```python
from pybricks.hubs import PrimeHub
from pybricks.pupdevices import Motor, ColorSensor, UltrasonicSensor, ForceSensor
from pybricks.parameters import Button, Color, Direction, Port, Side, Stop, Icon
from pybricks.robotics import DriveBase
from pybricks.tools import wait
 
hub = PrimeHub()
 
hub.speaker.beep(500, 300)       # pitido de 500 Hz durante 300 ms
hub.display.icon(Icon.HEART)     # corazón en la matriz de luces
wait(2000)                       # espera 2 segundos
hub.display.text("Hola")         # "Hola" desplazándose en la matriz
print("Listo!")                  # mensaje en la consola de la PC
```
 
`print` muestra el texto en la consola de la PC, no en el hub.
 
## Programa de prueba (Open Roberta)
 
```
start
  show image ♥ LED matrix
  wait ms 3000
```
 
El `wait` es necesario: al terminar el programa el hub borra la matriz de luces.
 
## Problemas frecuentes
 
| Mensaje / síntoma | Solución |
|---|---|
| "Activar Bluetooth para permitir el emparejamiento" | Encender el Bluetooth de Windows. |
| *Looks like you didn't select a device* | Tocar ▶ otra vez y elegir el hub (o **Volver a detectar**). |
| *Your robot is already connected to another instance* | Cerrar la pestaña de Pybricks u otros Labs, quitar el hub de Windows y apagar/encender el hub. |
| El hub no aparece en la lista | Falta instalar Pybricks (con firmware LEGO no aparece) o la PC no tiene Bluetooth. |
| La imagen desaparece al instante | Agregar `wait ms` al final del programa. |
| `info` muestra Name "-" y voltaje vacío | Normal: el SPIKE se conecta solo al tocar ▶. |
 
## Volver al firmware de LEGO
 
En [code.pybricks.com](https://code.pybricks.com) → configuración → **Restore Official LEGO Firmware**. Mientras tenga Pybricks, el hub no funciona con la app oficial de LEGO SPIKE.
 
## Referencias
 
- Guía SPIKE Prime: https://eliizquierdo.github.io/openRoberta-spike/Guia-OpenRoberta-SPIKE.html
- Open Roberta Lab: https://lab.open-roberta.org
- Pybricks: https://code.pybricks.com · documentación: https://docs.pybricks.com
- Guía para EV3: https://material-robotica.github.io/openRoberta-ev3/Guia-OpenRoberta-EV3.html
 
