# ESP32-TOOLS MODERN

Firmware multi-herramienta para ESP32 con interfaz moderna en pantalla TFT, pensado para aprendizaje, auditoria en redes propias y experimentacion con WiFi, Bluetooth BLE y radio 2.4 GHz.

> Usa este firmware solo en redes, dispositivos y laboratorios propios o con autorizacion explicita. Varias funciones pueden causar interferencia o capturar informacion sensible si se usan de forma incorrecta.

## Web flasher

Puedes flashear desde GitHub Pages con la pagina incluida en este repositorio:

https://pepeangell5.github.io/ESP32-TOOLS-MODERN/

Archivos usados por el flasher:

- `index.html`: pagina de flasheo con ESP Web Tools.
- `manifest.json`: manifiesto para ESP Web Tools.
- `firmware/firmware-merged.bin`: binario completo para flashear desde offset `0x0`.

## Hardware objetivo

- ESP32 Dev Module.
- Pantalla TFT SPI 480x320 usando `TFT_eSPI`.
- NRF24L01 principal.
- NRF24L01 secundario para funciones de radio/jammer con doble radio.
- Botones fisicos: `UP`, `OK`, `DOWN`.
- Framework Arduino con PlatformIO.

## Navegacion

- `UP` y `DOWN`: mover seleccion.
- Menus con scroll circular: al subir desde la primera opcion salta a la ultima, y al bajar desde la ultima vuelve a la primera.
- `OK`: seleccionar, iniciar o abrir detalles.
- `OK` mantenido: regresar, cancelar o salir cuando el menu lo indique.

## Funciones incluidas

### Menu principal moderno

- Menu principal redisenado en estilo minimalista.
- Fondo negro y texto blanco para mejorar lectura.
- Opciones visibles en pantalla.
- Seleccion con iluminacion/contorno.
- Navegacion circular.
- Submenus sin opcion extra de `BACK`; el regreso se hace con `OK` mantenido.

### WiFi Scanner

- Escanea redes WiFi 2.4 GHz cercanas.
- Lista SSID, canal, RSSI y tipo de seguridad.
- Muestra redes ocultas como `<HIDDEN>`.
- Detalles de red con BSSID, canal, frecuencia, RSSI y seguridad.
- Textos largos ajustados por ancho para evitar cortes feos.
- Scroll circular en la lista.
- Regreso con `OK` mantenido.

### WiFi Config

- Escaneo de redes para configurar conexion WiFi.
- Teclado virtual QWERTY para introducir contrasenas.
- Credenciales guardadas en NVS.
- Conexion automatica a red guardada.
- Opcion para olvidar red WiFi desde Settings.
- Selector sin opcion `CANCEL`; se cancela con `OK` mantenido.

### Radio Scanner

- Analizador de espectro 2.4 GHz usando NRF24L01.
- Modos visuales para actividad de radio.
- Vistas tipo espectro, waterfall y canales WiFi.
- Indicacion de actividad por canal.
- Salida con `OK` mantenido.

### Radio Jammer

- Adaptado para doble NRF24L01.
- Modo canal fijo WiFi.
- Modo TURBO para concentrar transmision.
- Modo WIDE para cubrir canales cercanos.
- Modo barrido total.
- Diagnostico de NRF1/NRF2 y pines SPI.
- Navegacion sin boton `BACK` visible; regreso con `OK` mantenido.
- Canal fijo con scroll circular del canal 1 al 13.

### Packet Monitor

- Monitor promiscuo de paquetes WiFi.
- Muestra paquetes por segundo.
- Indicadores de actividad.
- Cambio de canal con botones.
- Salida con `OK` mantenido.

### BLE Scanner

- Escanea dispositivos Bluetooth Low Energy.
- Lista nombre, MAC, RSSI y datos principales.
- Pantalla de detalles del dispositivo.
- Scroll circular.
- Salida con `OK` mantenido.

### BLE Spam

- Transmite advertisements BLE simulados.
- Modos para distintos tipos de popups/protocolos.
- Menu sin opcion `BACK`; regreso con `OK` mantenido.
- Pantalla activa con contador, dispositivo actual y tasa.

### BT Disruptor

- Escaneo de targets BLE.
- Seleccion de dispositivo objetivo.
- Modos de ataque BLE.
- Pantallas de ataque con tiempo, paquetes y tasa.
- Rescan como opcion de lista.
- Regreso con `OK` mantenido en selectores.

### Beacon Spam

- Emite beacons WiFi con SSIDs de listas internas.
- Modos tematicos de SSID.
- Cambio de canal durante ataque.
- Contador de beacons y tasa.
- Menu sin opcion `BACK`; regreso con `OK` mantenido.

### Deauther

- Escanea APs cercanos.
- Modo RAMBO para atacar multiples APs.
- Seleccion de AP.
- Escaneo de clientes.
- Ataque a todos los clientes o a cliente especifico.
- Rescan como opcion de lista.
- Regreso con `OK` mantenido en selectores.

### Evil Portal

- Portal cautivo con AP falso, DNS y servidor HTTP.
- Modo SIMPLE con SSIDs predefinidos.
- Modo CLONE + Deauth para clonar SSID/canal de una red de pruebas.
- Plantillas tipo Facebook, Google, Instagram y TikTok.
- Captura de usuario/email y password.
- Logs persistentes en NVS.
- Vista de logs con texto ajustado.
- Pantalla `LOG DETAIL` mejorada con campos claros para platform, email/user y password.
- Borrado de logs con confirmacion.
- Menus sin opcion `BACK`; regreso con `OK` mantenido.

### Probe Sniffer

- Captura probe requests.
- Lista SSIDs buscados por dispositivos cercanos.
- Muestra contador, RSSI y tiempo desde el ultimo avistamiento.
- Ordenamiento/acciones con `OK`.
- Salida con `OK` mantenido.

### Karma

- Captura probes durante una fase de escucha.
- Reanuncia SSIDs detectados como beacons.
- Muestra SSIDs capturados y estado del ataque.
- Salida con `OK` mantenido.

### Clock & Weather

- Reloj con sincronizacion NTP.
- Clima usando ubicacion aproximada por IP.
- Fallback de ubicacion configurado.
- Pantalla de datos de clima y hora.
- Salida con `OK` mantenido.

### Settings

- Activar/desactivar sonido.
- Ajustar volumen.
- Olvidar credenciales WiFi guardadas.
- Menu sin opcion `BACK`; regreso con `OK` mantenido.

### System Info

- Informacion del sistema.
- Uptime, memoria y datos de firmware.
- Salida con `OK` mantenido.

### About

- Informacion del proyecto.
- Creditos y detalles generales.
- Navegacion por contenido.

### Screensaver

- Protector de pantalla del ajolote.
- Se activa por inactividad.
- Se cierra con cualquier boton.

## Compilar localmente

Instala PlatformIO y ejecuta:

```powershell
pio run
```

El binario de aplicacion queda en:

```text
.pio/build/esp32dev/firmware.bin
```

El binario fusionado para el web flasher queda en:

```text
firmware/firmware-merged.bin
```

## Flasheo manual

Puedes flashear manualmente con PlatformIO:

```powershell
pio run -t upload
```

Tambien puedes usar el binario fusionado con una herramienta compatible con ESP32, escribiendolo desde offset `0x0`.

## Redes sociales

- Instagram: https://instagram.com/pepeangelll
- Facebook: https://www.facebook.com/esp32tools/
- GitHub: https://github.com/pepeangell5
