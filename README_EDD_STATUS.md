# ecq-app-config — EDD Status (Fase 1)

> **Fecha:** 2026-08-03 · **Modo:** análisis only  
> **Mega prompt:** [`../docs/EDD_MEGA_PROMPT_FASE1.md`](../docs/EDD_MEGA_PROMPT_FASE1.md)  
> **Rol:** Force-update remoto (versiones mínimas tienda) · **MANTENER**

---

## A. Identidad

| Campo | Valor |
|-------|--------|
| Propósito | JSON público que bloquea builds viejos de la app |
| Stack | Estático · GitHub Pages + Jekyll |
| URL | `https://saitamx.github.io/ecq-app-config/app-config.json` |
| Consumer | `ecq-front-app-native` `App.tsx` (solo `!__DEV__`, fail-open 12s) |

---

## B. Arquitectura

```
app-config.json · changelog.md · _config.yml · _layouts/ · assets/css/
```

Sin Node. Sin feature flags (futuro opcional).

---

## C. Tests

**0.** Falta: schema JSON on push · semver smoke · curl post-publish.

---

## D–E. Performance & cloud

Costo ~0 (Pages). Payload ~226 bytes. CDN puede atrasar minutos — documentado.

---

## F. Contrato `app-config.json`

```json
{
  "minAndroidVersion": "1.8.0",
  "minIosVersion": "1.8.0",
  "androidStoreUrl": "https://…",
  "iosStoreUrl": "https://…"
}
```

`min*` = mínima permitida (no “latest”).

---

## G. Eventos EDD

`ForceUpgradeRequired` · `StoreRedirect` · `ReleaseNotesPublished` · `FailOpenContinue`

---

## H. Mejoras

**P0:** ~~fix logo changelog (`logo.png` vs `ecq-logo.png`)~~ ✅ 2026-08-05 · checklist post-release.

**P1:** GitHub Action validate JSON/semver · alinear docs binario/OTA vs mins.

**P2:** campos extra solo si la app los consume (mensajes force-update, kill-switch).

---

## I. Workflow

1. Editar `app-config.json` (+ changelog)  
2. `git push` → Pages  
3. Esperar CDN · verificar URL live · probar build viejo  

**Estado EDD:** Tocarlo solo al retirar soporte de versiones en tienda.
