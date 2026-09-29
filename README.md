# ⚡ Método más fácil: obtener el EXE sin Visual Studio

No necesitas compilar localmente. Este repositorio incluye **Build EXE - One Click**.

En GitHub: **Actions → Build EXE - One Click → Run workflow → Artifacts → OnyxRFLab-EXE**.

El ZIP descargado contiene `OnyxRFLab.exe`. Consulta [BUILD_EXE.md](./BUILD_EXE.md).

---

# ONYX RF LAB · WINDOWS RF OBSERVATORY v1.0.1

**Created by Fran Gonzas · Software · Systems · Security**

Native Windows edition of Onyx RF Lab for **passive HackRF One observation** and Windows BLE situational awareness.

## Qué incluye

- C# / .NET 8 / WPF;
- live HackRF spectrum mediante `hackrf_sweep.exe`;
- 433 MHz, 2.4 GHz y barridos personalizados;
- presets 433 / 868 / 915 MHz / 2.4 GHz;
- control de frecuencia ±100 kHz y ±1 MHz;
- spectrum y waterfall gráficos;
- noise floor relativo, SNR y ocupación;
- candidatos RF y ancho de banda aproximado;
- baseline promediado de 12 barridos;
- eventos de cambio respecto al baseline;
- RF Tracks persistentes;
- observación de anuncios BLE mediante las APIs de Windows;
- nombre BLE, dirección Bluetooth, RSSI, fabricante y servicios cuando se anuncian;
- capturas IQ RX-only de 1 / 2 / 5 segundos;
- exportación JSON y CSV;
- publicación autocontenida como `OnyxRFLab.exe`.

## Método fácil

No instales Visual Studio para obtener el EXE.

1. Abre **Actions**.
2. Entra en **Build EXE - One Click**.
3. Pulsa **Run workflow**.
4. Espera al ✓ verde.
5. Descarga **OnyxRFLab-EXE** en **Artifacts**.
6. Descomprime el ZIP: dentro está `OnyxRFLab.exe`.

El workflow usa un equipo Windows de GitHub para compilar por ti.

## ⚠️ Requisito importante para usar HackRF

`OnyxRFLab.exe` es autocontenido y no necesita Visual Studio ni .NET instalado, pero **las herramientas de HackRF sí deben estar instaladas en Windows**.

Onyx necesita poder localizar:

```text
hackrf_info.exe
hackrf_sweep.exe
hackrf_transfer.exe
```

Si al iniciar una observación aparece:

```text
sweep error: no se encuentra hackrf_sweep.exe
```

significa que la aplicación funciona, pero Windows todavía no tiene disponibles las herramientas de HackRF o no están en una ubicación que Onyx pueda localizar.

### Comprobación rápida

Abre una terminal de Windows o Radioconda Prompt y ejecuta:

```powershell
hackrf_info
hackrf_sweep -h
```

- Si ambos comandos responden, las herramientas están instaladas.
- Si `hackrf_info` no detecta el dispositivo, revisa el driver **WinUSB** del HackRF.
- Si Windows indica que el comando no existe, instala las herramientas de HackRF para Windows.

Una opción práctica es **Radioconda**, que permite disponer de las herramientas HackRF en Windows.

Guía completa: [docs/HACKRF_WINDOWS.md](./docs/HACKRF_WINDOWS.md)

## Separación de identidad

La información BLE y las observaciones de espectro HackRF son fuentes distintas. Onyx no atribuye automáticamente una señal RF a una MAC/dirección Bluetooth.

## Alcance

```text
RX ONLY
NO RF TRANSMIT
NO JAMMING
NO REPLAY
NO AUTHENTICATION BYPASS
NO DEVICE IDENTITY FROM RF ENERGY ALONE
AUTHORIZED OBSERVATION ONLY
```

---

**Fran Gonzas · Creator**  
© 2026 Fran Gonzas


---


