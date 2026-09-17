# Pixel 3a XL en taller — estado y plan

> 17 sep 2026. Teléfono candidato de Miguel (sin pantalla), en proceso de
> reparación para poder verificarlo con fastboot.

## Identificación confirmada por USB
- **VID_18D1** = Google (confirmado por el bus USB de la laptop).
- **Serial (MTP):** `93QAX09U83`
- Modo en que aparece: **MTP** (arranca Android normal) con la placa armada.
- Modelos posibles del 3a XL: G020A / G020B / G020C / G020D (verificar en la
  tapa trasera o el marco; importa para pedir la pieza correcta).

## Estado físico
- **Sin pantalla** (para uso headless como placa no importa).
- **Placa madre extraída** por Miguel; se descubrió que el **puerto USB-C NO
  está en la placa madre**: vive en una **plaquita (daughterboard) abajo**,
  unida por **flex**.
- ⚠️ **INCIDENTE:** Miguel rompió el **flex/conector del puerto USB-C**.
- Consecuencia: sin USB-C no hay fastboot → **imposible verificar desbloqueo
  ni flashear** postmarketOS hasta repararlo.

## Plan elegido: MICROSOLDADURA
1. **Foto de acercamiento** del área del conector en la placa madre y del
   extremo del flex → determinar si se rompió:
   - el **flex** (se cambia la pieza completa: "Charging Port Flex Cable for
     Google Pixel 3a XL", ~5-15 USD), o
   - el **conector FPC de la placa** (reemplazo por microsoldadura).
2. Verificar si los **pads** de la placa siguen intactos (si se arrancaron
   pads, hay que hacer puentes = mucho más difícil).
3. Herramientas necesarias: estación de aire caliente (o cautín de punta
   fina), flux, malla desoldadora, alcohol isopropílico, pinzas, lupa o
   microscopio, y la pieza de repuesto.
4. Al quedar el USB funcional: **mantener Volumen Abajo + conectar USB** →
   bootloader → correr:
   ```
   fastboot getvar product
   fastboot getvar unlocked
   fastboot flashing get_unlock_ability
   ```

## Repuestos (enlaces)
- MobileSentrix: mobilesentrix.com/replacement-parts/google-pixel/pixel/google-pixel-3a-xl
- Cell Parts World: cellpartsworld.com/product/google-pixel-3a-xl-g020c-f-charging-port-flex/
- AliExpress: buscar "Pixel 3a XL charging port flex" (más barato, 2-4 semanas)

## Nota
Mientras se repara, sirve como **donante de partes** (batería, cámara, motor
de vibración). Y para la meta original (saber si es desbloqueable), la vía
más rápida sigue siendo un teléfono que arranque: 2 comandos de fastboot.
