# Obtener OnyxRFLab.exe — método fácil

No necesitas Visual Studio ni instalar .NET para compilar.

## Cada vez que quieras un EXE

1. Abre el repositorio en GitHub.
2. Entra en **Actions**.
3. Abre **Build EXE - One Click**.
4. Pulsa **Run workflow** y confirma con el botón verde.
5. Cuando aparezca el check verde, abre esa ejecución.
6. En **Artifacts**, descarga **OnyxRFLab-EXE**.
7. Descomprime el ZIP descargado: dentro está `OnyxRFLab.exe`.

Eso es todo.

## Qué hace GitHub por ti

GitHub usa un equipo Windows temporal, extrae el proyecto fuente, instala .NET 8, compila Onyx RF Lab y genera una aplicación `win-x64` autocontenida en un único EXE.

## Importante para usar HackRF

El EXE no sustituye al driver ni a las herramientas de HackRF. En el PC donde conectes el HackRF deben estar disponibles el driver WinUSB y las herramientas `hackrf_info`, `hackrf_sweep` y `hackrf_transfer`.
