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
- Solo para instalar el firmware en Windows: el controlador USB con **Zadig**, una vez por PC (requiere usuario administrador).

Para programar en clase no hace falta instalar nada: todo funciona desde el navegador.

## Archivos del repositorio

| Archivo | Para qué sirve |
|---|---|
| [`Guia-OpenRoberta-SPIKE.html`](https://material-robotica.github.io/OpenRoberta-SPIKE-Prime/Guia-OpenRoberta-SPIKE.html) | La guía paso a paso. |
| [`pybricks-primehub-v4.0.1.zip`](pybricks-primehub-v4.0.1.zip) | Firmware Pybricks **v4.0.1** para el SPIKE Prime. Se carga en el instalador **sin descomprimir**. |
| [`zadig-2.9.exe`](zadig-2.9.exe) | Instala el controlador USB de Windows necesario para la instalación manual del firmware. |

## ¿Por qué Pybricks v4.0.1 y no la última versión?

Desde **Pybricks v4.1.0**, el sensor de color acepta como máximo **8 colores** en `detectable_colors()`, y el código que genera Open Roberta le pasa **9**. Con la 4.1.0 o posterior, cualquier programa del Lab que tenga el sensor de color en la configuración **no arranca** y el hub no muestra ningún error.

Con la **v4.0.1** funciona correctamente. Mientras Open Roberta no corrija el error, **no aceptar** las actualizaciones de firmware que sugiere Pybricks.

## Resumen

| | SPIKE Prime (Pybricks) |
|---|---|
| Sistema en el robot | Firmware **Pybricks v4.0.1** instalado en el hub |
| Programa puente | Ninguno: conexión directa desde el navegador |
| Conexión | **Bluetooth** del navegador |
| Lenguaje generado | Python (MicroPython) |
| Tarjeta en el Lab | **Spike Prime / Robot Inventor / Pybricks** |

## Pasos

**Una sola vez por hub** ([Parte A de la guía](https://material-robotica.github.io/OpenRoberta-SPIKE-Prime/Guia-OpenRoberta-SPIKE.html)):

1. Descargar [`pybricks-primehub-v4.0.1.zip`](pybricks-primehub-v4.0.1.zip) (sin descomprimir).
2. En [code.pybricks.com](https://code.pybricks.com) → configuración → **Install Pybricks Firmware** → en el paso 1, **Advanced** → cargar el `.zip`. Debe decir *Firmware Version: ci-release-101-v4.0.1*.
3. En el paso 4, usar **Update manually** (la *Quick update* siempre instala la última versión). Poner el hub en modo actualización: apagado, mantener el botón de Bluetooth y conectar el USB hasta que la luz parpadee en rojo, verde y azul.
4. Si la ventana dice *No compatible devices found*, instalar el controlador con [`zadig-2.9.exe`](zadig-2.9.exe): **Options → List All Devices** → *LEGO Technic Large Hub in DFU Mode* → **WinUSB** → **Install Driver**.
5. Verificar que el hub **no** esté emparejado en *Configuración → Bluetooth y dispositivos* de Windows (si aparece, **Quitar**).
6. Comprobar la versión con el programa de abajo.

**En cada clase** ([Parte B de la guía](https://material-robotica.github.io/OpenRoberta-SPIKE-Prime/Guia-OpenRoberta-SPIKE.html)):

1. Activar el Bluetooth de Windows y cerrar cualquier pestaña de code.pybricks.com.
2. En el Lab elegir **Spike Prime / Robot Inventor / Pybricks**.
3. Armar el programa y tocar **▶** → elegir el hub → **Emparejar**.

## Comprobar la versión del firmware (Pybricks, Python)

Con el hub conectado por Bluetooth en code.pybricks.com:

```python
from pybricks import version
print(version)
```

En la consola tiene que aparecer `'4.0.1'`. La ventana *About* de Pybricks Code **no** muestra la versión del hub, sino la que trae el instalador.

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
| El programa no hace nada y la configuración tiene sensor de color | El hub tiene Pybricks 4.1.0 o posterior: instalar la **v4.0.1**. |
| Al instalar, *No compatible devices found* | Verificar el modo actualización (luz de colores) y el cable USB; si sigue, instalar el controlador con **Zadig**. |

## Volver al firmware de LEGO

En [code.pybricks.com](https://code.pybricks.com) → configuración → **Restore Official LEGO Firmware**. Mientras tenga Pybricks, el hub no funciona con la app oficial de LEGO SPIKE.

## Referencias

- Guía SPIKE Prime: https://material-robotica.github.io/OpenRoberta-SPIKE-Prime/Guia-OpenRoberta-SPIKE.html
- Open Roberta Lab: https://lab.open-roberta.org
- Pybricks: https://code.pybricks.com · documentación: https://docs.pybricks.com
- Firmware Pybricks (todas las versiones): https://github.com/pybricks/pybricks-micropython/releases
- Zadig: https://zadig.akeo.ie
- Guía para EV3: https://material-robotica.github.io/openRoberta-ev3/Guia-OpenRoberta-EV3.html
