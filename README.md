# ecq-app-config

JSON público que obliga a actualizar la app nativa cuando el binario queda por debajo del mínimo de tienda.

**Veredicto:** `SOPORTE`. Sirve viralidad solo en el sentido de que la app que abre el reel no se queda rota. Se toca al subir `minAndroidVersion` / `minIosVersion`.

Spec de ecosistema: [`../roadmap/spec-sdd-ecoquerai-v2.md`](../roadmap/spec-sdd-ecoquerai-v2.md).

## Specs vigentes

| ID | Resultado para la persona | Definición de hecho | Métrica | Estado |
|----|---------------------------|---------------------|---------|--------|
| CONFIG-MIN | No sigue usando un binario anterior al mínimo publicado | `app-config.json` declara `minAndroidVersion` y `minIosVersion`; la app compara al arranque y manda a la tienda | No medida (no se abrió la app) | Local y `https://saitamx.github.io/ecq-app-config/app-config.json` el 12 oct 2026: ambos `1.8.0`, Play `com.ecoquerai`, App Store `id6744342819` |

`min*` es la versión mínima permitida, no la última subida a la tienda. El changelog visible es [`changelog.md`](./changelog.md) (GitHub Pages).

## Fuera de alcance

- Flags, textos A/B o kill-switch. El JSON no los tiene y esta pasada no se comprobó que la app lea otros campos.
- Inscripciones, mapa, Quer e imágenes.
- OTA Revopush. Este repo no publica el bundle.

## Dependencias

- GitHub Pages del repo `Saitamx/ecq-app-config`.
- Único consumidor documentado: `ecq-front-app-native` al arranque.

## Cómo publicarlo

1. Editar `app-config.json`. Si el cambio es visible para quien actualiza, reflejarlo en `changelog.md`.
2. Push a la rama que sirve Pages.
3. Abrir la URL de arriba (el CDN puede tardar minutos).

No hay `npm`. No hay servidor.
