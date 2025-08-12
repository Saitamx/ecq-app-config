# ecoquerai-config

> **Repositorio público de configuración remota para la app móvil _EcoquerAI_.**

---

## ¿Para qué sirve?

Este repositorio contiene archivos JSON (y en el futuro YAML o similares) que la app **EcoquerAI** descarga al iniciarse para:

| Uso | Descripción | Ventaja |
|-----|-------------|---------|
| **Versión mínima (`minAndroidVersion`, `minIosVersion`)** | Define qué versión de la app es obligatoria por plataforma. Si el usuario tiene una versión anterior, se muestra una pantalla que lo dirige a Play Store / App Store. | Permite "jubilar" versiones antiguas **sin** volver a compilar ni publicar un nuevo binario. |
| **Enlaces a las tiendas** | `androidStoreUrl` y `iosStoreUrl` se usan como destino del botón **Actualizar ahora**. | Si cambias la ficha de la tienda, solo editas el JSON aquí. |
| **Flags de funciones (próximamente)** | Activar/desactivar features, A/B testing, textos dinámicos, etc. | Control total desde la web, cambios instantáneos. |

---

## Estructura del archivo principal

```jsonc
{
  "minAndroidVersion": "1.7.1",
  "minIosVersion": "1.4.0",
  "androidStoreUrl": "https://play.google.com/store/apps/details?id=com.ecoquerai",
  "iosStoreUrl": "https://apps.apple.com/cl/app/ecoquerai/id6744342819"
}
```

---

## Versiones actuales

- **Android**: `1.7.1` (Play Store)
- **iOS**: `1.4.0` (App Store)

---

## ¿Cómo funciona?

1. **La app se inicia** y descarga automáticamente `app-config.json`
2. **Compara versiones**: `DeviceInfo.getVersion()` vs `minAndroidVersion`/`minIosVersion`
3. **Si necesita actualizar**: Muestra `ForceUpdateScreen` con enlaces a las tiendas
4. **Si está actualizada**: Continúa normalmente

---

## URLs de acceso

- **Configuración**: https://saitamx.github.io/ecq-app-config/app-config.json
- **Changelog**: https://saitamx.github.io/ecq-app-config/changelog.md
- **Repositorio**: https://github.com/Saitamx/ecq-app-config
