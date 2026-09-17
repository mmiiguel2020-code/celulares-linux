# Pixel 3a XL en taller — estado y plan

> 17 sep 2026. Teléfono candidato de Miguel (sin pantalla), en proceso de
> reparación para poder verificarlo con fastboot.

## Identificación confirmada por USB
- **VID_18D1** = Google (confirmado por el bus USB de la laptop).
- **Serial (MTP):** `93QAX09U83`
- Modo en que aparece: **MTP** (arranca Android normal) con la placa armada.
- Modelos posibles del 3a XL: G020A / G020B / G020C / G020D (verificar en la
  tapa trasera o el marco; importa para pedir la pieza correcta).

## ✅ MODELO CONFIRMADO 17 sep: **Pixel 3a XL** (variante G020A/B)

Prueba documental: **etiqueta de la batería** (foto del 17 sep):
- Modelo: **`G020A-B` (1ICP5/64/74)** → código del **Pixel 3a XL**
- Capacidad: **3700 mAh / 14.24 Wh** → el Pixel 3a normal tiene 3000 mAh
- Fabricante: Huizhou Desay Battery Co., Ltd (proveedor original)
- N/P batería: `G8230010801` / `G82300108012AA`
- Certificaciones: PSE, R33724, UL, CE, BSMI

→ Al pedir repuestos usar SIEMPRE la variante **"For Pixel 3a XL"**
(no "Pixel 3a" ni "Pixel 3 XL").

## Piezas del teléfono (inventario del 17 sep)
- ✅ Placa madre (conector FPC visiblemente INTACTO en macros)
- ✅ Flex `G653-00595-02` (2018/08/08) — **intacto**, etiqueta legible
- ❌ **FALTA la plaquita del puerto USB-C** (lo que Miguel llama "la placa")
- ❌ Falta la pantalla (irrelevante para uso headless)
- ❌ Falta la batería (está fuera; presente pero no instalada)

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

## ACTUALIZACION 17 sep — pieza ENCONTRADA (AliExpress)

- Tienda: **E-KINLIN** — "Puerto de carga USB conector de clavija cargador
  Cable flexible para Google Pixel 3a XL"
- Variante correcta seleccionada: **For Pixel 3a XL** ✅
- Precio: **MX$80.90** (~4.40 USD), **envío gratis** en el primer pedido,
  5.0★, 43 vendidos, devoluciones gratis.
- Confianza extra: la etiqueta del flex del listado es `G653-0...`, la MISMA
  familia que la etiqueta de la placa de Miguel (`G653-00595-02`).
- DECISION: comprar **2 piezas** (repuesto, por lo barato).
- ⚠️ Verificar en el carrito que diga **3a XL** (no "3a" ni "3 XL").

### Inspección de la placa (fotos 17 sep, con lupa)
- El **conector FPC de la placa madre se ve INTACTO** (fila de pines dorados
  completa, carcasa presente) → si es así, **la pieza nueva solo se enchufa**
  (cero microsoldadura). La vía de soldar cables a puntos de prueba queda
  como plan B.
- El flex de la placa (etiqueta `G653-00595-02`, 2018-08-08) también se vio
  completo en las macros.
- Sobre los **puntos de prueba redondos (1 mm)**: NO se pueden identificar
  (VBUS/GND/D+/D-) por foto. Método seguro: GND por continuidad al blindaje;
  los otros 3 con **el flex como mapa** (medir del pin del USB-C del flex a
  sus contactos FPC y de ahí a los test points de la placa).

## Repuestos (enlaces)
- MobileSentrix: mobilesentrix.com/replacement-parts/google-pixel/pixel/google-pixel-3a-xl
- Cell Parts World: cellpartsworld.com/product/google-pixel-3a-xl-g020c-f-charging-port-flex/
- AliExpress: buscar "Pixel 3a XL charging port flex" (más barato, 2-4 semanas)

## Nota
Mientras se repara, sirve como **donante de partes** (batería, cámara, motor
de vibración). Y para la meta original (saber si es desbloqueable), la vía
más rápida sigue siendo un teléfono que arranque: 2 comandos de fastboot.
