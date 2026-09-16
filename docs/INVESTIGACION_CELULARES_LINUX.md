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
