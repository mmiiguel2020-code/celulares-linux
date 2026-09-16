# Investigación: celulares económicos (2017+) para Linux libre como "placas Pi"

> 15 sep 2026. Objetivo de Miguel: modelos de celular usados/nuevos, 2017 →
> actual, con bootloader DESBLOQUEABLE para instalar Linux (postmarketOS /
> Droidian / Ubuntu Touch) y usarlos sin restricciones con software libre,
> como sustitutos de Raspberry Pi / Teensy.

## 1. Criterios de selección

1. **Bootloader desbloqueable sin peleas** (fastboot o herramienta oficial; NO
   variantes de operador de EE.UU. ni Samsung con Knox/OEM bloqueado).
2. **Soporte postmarketOS** en categoría "main" o "community" con imágenes
   precompiladas (postmarketos.org/install).
3. **Precio de usado** bajo en México (Mercado Libre / Facebook Marketplace).
4. **CPU y RAM** útiles (2017+ Snapdragon = suficiente para Linux de escritorio).
5. **USB Networking** funcional (SSH por cable = usar como placa sin pantalla).

## 2. Los 3 candidatos confirmados (wiki postmarketOS, 15 sep 2026)

| | Google Pixel 3a | OnePlus 6 / 6T | Xiaomi POCO F1 |
|---|---|---|---|
| Año | 2019 | 2018 | 2018 |
| CPU | SDM670 (octa) | **SDM845 (octa)** | SDM845 (octa) |
| RAM | 4 GB | **6/8 GB** | 6/8 GB |
| pmOS | community, imágenes listas | community, imágenes listas | community, imágenes listas |
| Kernel mainline | ✅ 6.18 | ✅ | ✅ |
| Desbloqueo | ✅ **`fastboot flashing unlock`, SIN códigos ni cuentas** | ✅ `fastboot oem unlock` (salvo variante T-Mobile US) | ⚠️ cuenta Xiaomi + Mi Unlock + **días de espera** |
| Estabilidad de arranque | ✅ buena | ✅ buena | ❌ ~80 % de arranques se cuelgan con kernels recientes (reintentar) + WiFi/módem se caen solos |
| Precio usado MX aprox. | ~900-1,400 | ~1,200-1,800 | ~900-1,400 |
| Jack 3.5 mm | ✅ | ❌ (solo USB-C) | ✅ |
| Unixbench (wiki) | 4417 | 6487 | 6565 |

**Veredictos:**
- 🥇 **Para empezar sin fricción: Google Pixel 3a.** El desbloqueo más simple
  del mercado, puerto maduro (kernel 6.18), barato. Menos RAM (4 GB).
- 🥈 **Para potencia: OnePlus 6/6T.** SDM845 + 6-8 GB RAM, desbloqueo fácil,
  soporte excelente. El "portátil de trabajo" según la propia wiki.

## 2.5 Franja económica: < 100 USD (~1,900 MXN) — solo USADOS

**Nuevos por menos de 100 USD NO existen para esto:** esa franja nueva es
MediaTek/Unisoc con bootloader cerrado y cero soporte Linux. El camino de
presupuesto es 100 % usado.
Dato real de Miguel (15 sep 2026): compró un celular NUEVO "con todo lo
normal de Android" en Mercado Libre MX por 600 MXN (~30 USD) — ese equipo es
de la categoría cerrada (bootloader de fábrica, sin comunidad): perfecto
ejemplo de que NUEVO barato = Android básico, mientras USADO al mismo precio
= Pixel/OnePlus con Linux desbloqueable.
Ejemplo CONFIRMADO (15 sep): "5 pulgadas, 32 GB, 2 GB RAM, 3G, Android Go 14,
Unisoc SC7731E, 580 MXN nuevo" → ❌ DESCARTADO: (1) bootloader cerrado sin
desbloqueo conocido; (2) chip de 2017 ARMv7 32-bit sin soporte mainline
Linux (ni siquiera aparece en la lista de pmOS); (3) 2 GB/32-bit/3G =
máquina de WhatsApp, no computadora. Regla práctica: si dice "Android Go"
o "Unisoc SC77xx/MediaTek A-series", es de la categoría cerrada.

| Modelo | Precio usado aprox. | Por qué |
|---|---|---|
| **Pixel 3a / 3a XL** | 40-80 USD | ⭐ desbloqueo de 1 comando, puerto maduro, jack 3.5 |
| **Pixel 3 / 3 XL** (blueline/crosshatch) | 40-80 USD | SDM845, puerto confirmado en pmaports v25.12 |
| **OnePlus 5 / 5T** | 40-60 USD | community, lo más barato de OnePlus desbloqueable |
| **OnePlus 6 / 6T** | 60-90 USD | SDM845 + 6-8 GB RAM, el de más potencia del rango |
| Poco F1 | 50-70 USD | solo si es ganga: desbloqueo Xiaomi engorroso + arranque flaky |
| Galaxy S7 / A5 2017 (Exynos intl.) | 30-60 USD | ports Exynos existen, pero variantes regionales/Knox = para manos expertas |

**Top por presupuesto:** Pixel 3a (más fácil) o OnePlus 6 (más potencia) —
ambos caben sobrados en <100 USD usados. Los SDM845 usados ya andan por
~200 yuan (~28 USD) en China: el mercado de segunda mano está saturado de
ellos, buen momento para comprar.

Referencias extra del hallazgo: pmOS v26.06 ya cubre **254 dispositivos**
(techtimes.com) y hay movimiento de "cyberdecks" reciclando viejos Pixel
con pmOS (hackster.io "HaPlay GO Zero").
- 🥉 **Poco F1: solo si aparece MUY barato.** Mismo chip que el OP6, pero el
  desbloqueo de Xiaomi es engorroso y tiene problemas de arranque/WiFi
  documentados.

## 3. Menciones honrosas (menos verificadas aquí)

- **OnePlus 5/5T** (2017): community, más viejo, más barato.
- **Samsung Galaxy A5/A3 2017 (Exynos)**: community en pmOS, pero Exynos y
  Knox → solo variantes no-EE.UU.; más pelea de lo que vale.
- **PinePhone / PinePhone Pro**: no es "celular 2017+", es Linux de fábrica;
  usado ~1,500-2,500 MXN. Opción "cero pelea" si el presupuesto alcanza.

## 4. Distribuciones Linux para celulares (2017+)

- **postmarketOS** (Alpine) — la referencia en mainline; Phosh/Plasma Mobile.
- **Droidian** (Debian) — drivers Halium; más compatibilidad de hardware, menos
  "mainline puro".
- **Ubuntu Touch (UBports)** — fácil de instalar (instalador oficial), menos
  libre que pmOS (Halium).
- **Mobian** (Debian) — como Droidian, foco PinePhone/Pocophone.

## 5. Advertencias HONESTAS (para usarlos "como Pi")

1. **USB OTG está ROTO en los 3 candidatos** en pmOS: no puedes enchufarles
   periféricos USB (teclado, MIDI, DAC USB) todavía. Sí funciona USB
   NETWORKING (SSH hacia la PC por cable). → Para el proyecto acordeón, la
   ruta con celular-linux sería MIDI por WiFi (Ruta E), no USB.
2. **Batería:** carga limitada (~1.5 A en Pixel 3a), sin todas las protecciones
   de Android. No dejarlos conectados 24/7 sin supervisión al principio.
3. **Módem/llamadas:** funcionan "parcial"; para uso como placa no importa.
4. **Cámara/huella:** parciales/rotas. Irrelevante como placa.
5. El proceso de instalación usa `fastboot` desde la PC (Linux o Windows) y
   borra el Android (o dual-boot con menos espacio).

## 6. Recomendación final

> **Comprar un Google Pixel 3a usado** (o el 3a XL por pantalla/batería) como
> primera unidad: desbloqueo instantáneo, puerto maduro, precio bajo. Si se
> necesita más RAM/potencia → **OnePlus 6/6T**. Evitar el Poco F1 salvo ganga.

## 7. Fuentes (verificadas 15 sep 2026)

- wiki.postmarketos.org/wiki/OnePlus_6_(oneplus-enchilada)
- wiki.postmarketos.org/wiki/Google_Pixel_3a_(google-sargo)
- wiki.postmarketos.org/wiki/Xiaomi_POCO_F1_(xiaomi-beryllium)
- postmarketos.org/install (imágenes precompiladas)
- docs.droidian.org (FAQ de Droidian)
- Lista de dispositivos: wiki.postmarketos.org/wiki/Devices

## 8. Dónde comprar (alcance local / nacional / internacional)

### 8.1 Local (Cd. Obregón / Sonora)
- **Facebook Marketplace** con radio 50-100 km: buscar "Pixel 3a", "Pixel 3",
  "OnePlus 6". Probabilidad baja (son equipos raros en la región), pero hay
  sorpresas y se puede probar el equipo EN PERSONA antes de pagar.
- Casas de empeño locales: poca probabilidad para Pixel/OnePlus (dominan
  iPhone/Samsung); vale una vuelta si ya se está cerca.

### 8.2 Nacional (México, con envío)
- **Mercado Libre México**: buscar "Pixel 3a usado", "OnePlus 6 8GB",
  "Pixel 3 desbloqueado". Filtrar por "Usado/Reacondicionado", leer
  reputación del vendedor y devoluciones. OJO: en ML-MX suelen estar
  MÁS CAROS que en eBay (a veces el doble); comparar antes.
- **Facebook Marketplace nacional** (con envío): mismos términos de búsqueda.
- Tiendas mexicanas de reacondicionados en línea (revisar cuáles tienen
  Pixel/OnePlus en catálogo).

### 8.3 Internacional (el mejor precio-calidad)
- **eBay US con envío a México** ⭐: filtrar "Ships to Mexico" (el programa
  de envío internacional muestra impuestos por adelantado). Pixel 3a
  desbloqueado ~40-70 USD + ~15-25 USD de envío. Revisar: vendedor con
  feedback alto, "Factory Unlocked", devoluciones aceptadas.
- **AliExpress**: Pixel 3a/OnePlus 6 reacondicionados con envío a México
  (2-4 semanas); preferir vendedores con almacén en EE.UU. y miles de
  ventas. (Ver listado de Xataka sobre Pixels en AliExpress.)
- **Amazon US**: solo artículos con "envío internacional elegible"; los
  impuestos se calculan al pagar.

### 8.4 ⚠️ Cómo NO equivocarse al comprar (crítico para el desbloqueo)
1. **Pixel: comprar SOLO "Factory Unlocked" (edición Google).** Los Pixel de
   Verizon vienen con bootloader BLOQUEADO y no se desbloquean (igual que el
   Note 8 de Miguel). Preguntar al vendedor o revisar el modelo exacto.
2. **OnePlus 6: evitar la variante T-Mobile US** (pide código de desbloqueo);
   preferir A6003 (internacional/global).
3. Preguntar siempre al vendedor: "¿bootloader desbloqueable? (OEM unlocking)".
4. Revisar: batería de salud razonable, pantalla sin quemaduras (AMOLED),
   botones firmes, sin cuenta Google bloqueada (FRP) — pedir foto del menú
   de ajustes si es Marketplace/eBay con fotos dudosas.
5. Presupuesto total objetivo: **equipo + envío < 100 USD** (Pixel 3a lo
   cumple sobrado; OnePlus 6/6T también en la mayoría de listados).
