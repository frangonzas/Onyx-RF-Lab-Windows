# Onyx RF Lab Windows · Architecture

## 1. Objetivo

Onyx RF Lab Windows es un observatorio RF de escritorio orientado a recepción pasiva con HackRF One. La arquitectura separa explícitamente adquisición RF, interpretación y agregación temporal, presentación, inventario Bluetooth de Windows y evidencia/exportación.

## 2. Capas

```text
┌─────────────────────────────────────────────────────────────┐
│                         WPF UI                              │
│ MainWindow · Spectrum · Waterfall · History · Gauge        │
├─────────────────────────────────────────────────────────────┤
│                      MainViewModel                          │
│ Session state · commands · metrics · tracks · events       │
├─────────────────────────────────────────────────────────────┤
│                         Services                            │
│ HackRfService · SweepParser · BluetoothScannerService      │
│ HackRfToolLocator · ExportService                          │
├─────────────────────────────────────────────────────────────┤
│                     External tools                          │
│ hackrf_info · hackrf_sweep · hackrf_transfer              │
├─────────────────────────────────────────────────────────────┤
│                         Hardware                            │
│                         HackRF One                          │
└─────────────────────────────────────────────────────────────┘
```

## 3. Presentation layer

La aplicación utiliza **WPF sobre .NET 8**. Los controles gráficos representan espectro, waterfall, historial temporal peak/noise e indicador de situación RF.

La UI consume estado del ViewModel; no debe asumir que un bin de frecuencia equivale a una identidad de dispositivo.

## 4. ViewModel

`MainViewModel` coordina el perfil RF activo, rango de barrido, frecuencia de enfoque, ganancias, umbrales, frames, baseline, candidatos, RF Tracks, eventos, dispositivos BLE observados por Windows y rutas de evidencia/exportación.

## 5. RF acquisition

### HackRfToolLocator

Localiza:

```text
hackrf_info.exe
hackrf_sweep.exe
hackrf_transfer.exe
```

La aplicación diferencia un fallo de localización del ejecutable de un fallo del dispositivo.

### HackRfService

Gestiona los procesos de HackRF y su ciclo de vida. La recepción en vivo utiliza `hackrf_sweep`; las capturas IQ RX-only utilizan `hackrf_transfer`.

### SweepParser

Convierte la salida de `hackrf_sweep` en datos estructurados de frecuencia/potencia.

## 6. Processing pipeline

```text
hackrf_sweep stdout
       │
       ▼
   SweepParser
       │
       ▼
Spectrum frame
       │
       ├── metrics
       ├── waterfall
       ├── history
       ├── candidate extraction
       ├── baseline comparison
       └── persistent RF tracks
```

## 7. Bluetooth layer

`BluetoothScannerService` utiliza capacidades de Windows para observar información BLE disponible en el host.

Esta capa se mantiene separada del motor HackRF. Un nombre, dirección o servicio BLE visto por Windows no se asigna automáticamente a una señal del espectro.

## 8. Evidence layer

`ExportService` serializa información de sesión para análisis posterior: espectro, métricas, candidatos, RF Tracks, eventos, inventario Bluetooth observado y metadatos de sesión.

Las capturas IQ permanecen como archivos de señal independientes para análisis autorizado fuera de línea.

## 9. Build pipeline

GitHub Actions produce una publicación:

```text
Target: win-x64
.NET: 8
Mode: self-contained
Output: OnyxRFLab.exe
```

## 10. Boundary

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

**Onyx RF Lab · Windows RF Observatory**  
**FranGonzas · Creator**  
© 2026 FranGonzas
