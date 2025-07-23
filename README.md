# ecoquerai-config

> **Repositorio público de configuración remota para la app móvil _EcoquerAI_.**

---

## ¿Para qué sirve?

Este repositorio contiene archivos JSON (y en el futuro YAML o similares) que la app **EcoquerAI** descarga al iniciarse para:

| Uso | Descripción | Ventaja |
|-----|-------------|---------|
| **Versión mínima (`minAppVersion`)** | Define qué versión de la app es obligatoria. Si el usuario tiene una versión anterior, se muestra una pantalla que lo dirige a Play Store / App Store. | Permite “jubilar” versiones antiguas **sin** volver a compilar ni publicar un nuevo binario. |
| **Enlaces a las tiendas** | `androidStoreUrl` y `iosStoreUrl` se usan como destino del botón **Actualizar ahora**. | Si cambias la ficha de la tienda, solo editas el JSON aquí. |
| **Flags de funciones (próximamente)** | Activar/desactivar features, A/B testing, textos dinámicos, etc. | Control total desde la web, cambios instantáneos. |

---

## Estructura del archivo principal

```jsonc
{
  "minAppVersion": "1.6.9",
  "androidStoreUrl": "https://play.google.com/store/apps/details?id=com.ecoquerai",
  "iosStoreUrl":    "https://apps.apple.com/cl/app/ecoquerai/id6744342819"
}
