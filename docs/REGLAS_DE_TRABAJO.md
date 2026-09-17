# REGLAS DE TRABAJO (pedidas por Miguel)

> Reglas de comportamiento del agente en este proyecto. Se suman a las
> directrices de la pegatina del escritorio.

## 1. ⭐ No pedirle a Miguel lo que el agente puede hacer solo
**(17 sep 2026)** — Textual: *"no me mandes a hacer algo que tu puedes hacer"*.

**Antes de pedirle una acción, el agente agota lo que puede hacer por su cuenta:**

| El agente SÍ puede y SÍ debe hacerlo solo |
|---|
| Buscar en internet (precios, tiendas, datasheets, compatibilidad) |
| **Ver imágenes**: descargar fotos/screenshots (de la laptop o del celular vía `adb pull`) y analizarlas con `read_image` |
| OCR de capturas (script de Windows OCR en `$env:TEMP`) |
| Comparar listados de tiendas, validar variantes y precios |
| Leer/escribir archivos, revisar repos, `git log`, compilar, ejecutar comandos en la laptop |
| Medir/verificar por software (puertos COM, USB, discos, checksums MD5) |

**Solo pedirle a Miguel lo que exige SUS MANOS o su presencia física:**

- Conectar, soldar o mover cables
- Presionar botones (RST, combinaciones de bootloader)
- Medir con multímetro u osciloscopio
- Aceptar cuadros de UAC / permisos de Windows
- Autorizar y estar presente en el flasheo de firmware
- Tocar el acordeón o el instrumento

**Regla práctica:** si la tarea se resuelve con información, el agente la
resuelve; si se resuelve con manos, se le pide a Miguel — y explicando por qué
solo él puede hacerla.

## 2. Permiso antes de grabar firmware
Siempre. Sin excepción (ver pegatina).

## 3. No inventar pines ni cableado
Los pines se confirman con multímetro o con datos verificados del proyecto.

## 4. Español y paso a paso
Miguel es músico, no ingeniero: explicaciones cortas, numeradas y sin jerga
innecesaria.
