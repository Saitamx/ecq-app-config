# EcoquerAI App Config (`ecq-app-config`)

| | |
|--|--|
| **Estado ecosistema** | **MANTENER** — cambios raros a propósito |
| **Prioridad 90 días** | Solo tocar al forzar min version en tiendas |
| **Documento maestro** | [`../README.md`](../README.md) |

> Config **remota pública** (GitHub Pages) para force-update de la app nativa. Julio 2026.  
> No hay servidor: solo JSON estático.

| | |
|--|--|
| **URL live** | https://saitamx.github.io/ecq-app-config/app-config.json |
| **Repo** | https://github.com/Saitamx/ecq-app-config |
| **Consumidor** | `ecq-front-app-native` al arranque (`ForceUpdateScreen`) |

---

## Contenido actual (`app-config.json`)

```json
{
  "minAndroidVersion": "1.8.0",
  "minIosVersion": "1.8.0",
  "androidStoreUrl": "https://play.google.com/store/apps/details?id=com.ecoquerai",
  "iosStoreUrl": "https://apps.apple.com/cl/app/ecoquerai/id6744342819"
}
```

Play Store y App Store live: **1.8.0**.  
`min*` = versión **mínima permitida** (bloquea más viejas), no la última publicada.

---

## Cómo funciona

1. La app descarga este JSON al iniciar.
2. Compara `DeviceInfo.getVersion()` vs `minAndroidVersion` / `minIosVersion`.
3. Si es menor → pantalla de actualización con store URLs.
4. Si cumple → continúa (auth / tabs / OTA soft).

---

## Cómo publicar un cambio

1. Editar `app-config.json` en este repo.
2. Push a la rama que sirve GitHub Pages.
3. Verificar URL live (cache CDN: esperar unos minutos).
4. Probar con un build viejo o mock de versión.

**Cuidado:** subir `min*` a `1.8.0` obliga a todos por debajo de esa versión a ir a la tienda.

---

## Futuro

Flags de features, textos, A/B — aún no en el JSON; la app solo usa min versions + store URLs hoy.

---

## Relacionados

- App: `../ecq-front-app-native/README.md`
- Ecosistema: `../README.md`
