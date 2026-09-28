# HackRF en Windows 11 — preparación para Onyx RF Lab

**Onyx RF Lab Windows** utiliza las herramientas de HackRF para recibir y analizar el espectro.

## 1. Qué necesita Onyx

El PC debe disponer de:

```text
hackrf_info.exe
hackrf_sweep.exe
hackrf_transfer.exe
```

Estas herramientas son externas a `OnyxRFLab.exe`.

## 2. Error: "sweep error: no se encuentra hackrf_sweep.exe"

Este mensaje significa:

- Onyx RF Lab ha arrancado correctamente.
- El motor intenta iniciar una observación RX.
- Windows no encuentra `hackrf_sweep.exe`.

No significa que la interfaz de Onyx esté dañada.

## 3. Instalación sencilla

Una opción práctica en Windows es instalar **Radioconda** y las herramientas de HackRF.

Después de instalar las herramientas, cierra Onyx RF Lab y vuelve a abrirlo.

## 4. Comprobar las herramientas

Abre una terminal de Windows o Radioconda Prompt:

```powershell
hackrf_info
```

Después:

```powershell
hackrf_sweep -h
```

También puedes comprobar:

```powershell
hackrf_transfer -h
```

Si los tres comandos responden, el software básico está disponible.

## 5. Comprobar el HackRF físico

Conecta el HackRF One por USB y ejecuta:

```powershell
hackrf_info
```

Debe aparecer información del dispositivo.

Si el ejecutable existe pero el dispositivo no aparece, comprueba el controlador USB. En Windows, HackRF se utiliza normalmente mediante **WinUSB**.

## 6. Driver USB

Si es necesario corregir el driver, puede utilizarse Zadig para asignar **WinUSB** al dispositivo HackRF.

Evita cambiar drivers de otros dispositivos USB por error: selecciona expresamente el HackRF.

## 7. Volver a Onyx

Cuando `hackrf_info` y `hackrf_sweep -h` funcionen:

1. Cierra Onyx RF Lab.
2. Vuelve a ejecutar `OnyxRFLab.exe`.
3. Conecta HackRF One.
4. Selecciona, por ejemplo, **433 MHz**.
5. Pulsa **START RX**.

Onyx deberá poder iniciar `hackrf_sweep.exe` y comenzar a llenar:

- Spectrum
- Waterfall
- Noise floor
- Peak
- Occupancy
- Signal candidates
- RF Tracks

## 8. Nota sobre Bluetooth

El escáner Bluetooth de Windows y las observaciones de espectro HackRF son fuentes distintas. Onyx no atribuye automáticamente un pico RF a una dirección Bluetooth concreta.

## 9. Alcance de seguridad

```text
RX ONLY
NO RF TRANSMIT
NO JAMMING
NO REPLAY
NO AUTHENTICATION BYPASS
AUTHORIZED OBSERVATION ONLY
```

---

**Onyx RF Lab Windows · Fran Gonzas**
