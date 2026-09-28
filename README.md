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

## Para usar HackRF

El PC donde ejecutes Onyx necesita que el HackRF esté correctamente configurado con WinUSB y que estén disponibles:

```text
hackrf_info.exe
hackrf_sweep.exe
hackrf_transfer.exe
```

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
