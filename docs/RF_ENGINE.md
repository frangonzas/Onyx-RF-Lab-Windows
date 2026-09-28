# Onyx RF Lab Windows · RF Engine

## 1. Propósito

El motor RF transforma barridos de HackRF One en información temporal y espectral utilizable por un operador. Su objetivo es mostrar qué energía aparece en la banda, qué actividad persiste, qué cambia frente a una referencia y qué evidencia debe conservarse.

No intenta inferir identidad de transmisor únicamente a partir de potencia, frecuencia o persistencia.

## 2. Perfiles de observación

La interfaz ofrece perfiles rápidos para **433 MHz**, **868 MHz**, **915 MHz**, **2.4 GHz** y **Custom sweep**.

## 3. Spectrum

Cada frame representa potencia relativa distribuida por frecuencia. La vista permite inspeccionar nivel de fondo, picos, actividad localizada, cambios de forma espectral y relación con la frecuencia seleccionada.

Los valores deben interpretarse como **relativos** salvo calibración completa de la cadena RF.

## 4. Waterfall

```text
X → frecuencia
Y → tiempo
intensidad → potencia relativa
```

Permite distinguir actividad continua, periódica, señales breves y cambios de ocupación.

## 5. Métricas

- **Noise floor:** referencia relativa del fondo observado.
- **Peak:** región de mayor potencia del frame.
- **SNR:** separación relativa entre señal candidata y fondo.
- **Occupancy:** proporción de banda que supera el criterio operativo de actividad.

## 6. Baseline

El baseline captura una referencia temporal de la banda. Onyx utiliza una media de **12 frames** para estabilizar la referencia y comparar observaciones posteriores.

## 7. RF Candidates

Un candidato RF representa una región espectral que merece seguimiento. Puede conservar frecuencia central, peak, SNR, ancho de banda aproximado y relación con baseline.

Un candidato no equivale a un dispositivo identificado.

## 8. Persistent RF Tracks

Los tracks agrupan estadísticamente candidatos recurrentes. La tabla incluye center MHz, hits, persist %, max SNR, peak dB, mean BW kHz, first seen, last seen y reference.

## 9. Baseline Change Events

Los cambios respecto a la referencia pueden registrarse con timestamp, nivel, tipo, frecuencia, potencia actual, delta, SNR y ancho de banda.

## 10. BLE channel references

En 2.4 GHz se muestran referencias de canales BLE para contexto visual. No demuestran que un pico sea un dispositivo Bluetooth concreto ni lo vinculan con una dirección observada por Windows.

## 11. IQ capture

Las capturas IQ se realizan en recepción mediante `hackrf_transfer` y se reservan para análisis autorizado fuera de línea. El flujo no habilita transmisión ni replay.

## 12. Limitaciones de interpretación

No debe afirmarse, solo a partir del observatorio RF:

- identidad inequívoca del transmisor;
- dirección MAC de una señal;
- potencia absoluta calibrada;
- protocolo exacto sin decodificación protocol-aware;
- procedencia física exacta sin técnicas adicionales.

## 13. Operational model

```text
Observe
  ↓
Establish baseline
  ↓
Detect candidates
  ↓
Track persistence
  ↓
Record events
  ↓
Capture/export evidence
  ↓
Analyze offline when required
```

---

**Onyx RF Lab · Windows RF Observatory**  
**FranGonzas · Creator**  
© 2026 FranGonzas
