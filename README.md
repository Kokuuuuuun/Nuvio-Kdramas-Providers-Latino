# Doramas Nuvio Providers

Providers para **Nuvio Media Hub** con contenido de Doramas Coreanos, Chinos, Japoneses, Asiáticos y más en **Español Latino**.

Resolvers avanzados implementados desde cero con soporte para múltiples servidores de video.

---

## ✅ Providers Activos

### 🎭 DoramasFlix (`doramasflix.in`)
- **Estado:** ✅ Funcional
- **Contenido:** Doramas Coreanos, Chinos, Japoneses y Asiáticos
- **Idioma:** Español / Latino
- **Resolvers:** VOE, StreamWish, VidHide/Do7Go, OkRu, Filemoon
- **Búsqueda:** Usa TMDB API para obtener nombre exacto → busca en DoramasFlix API
- **Versión:** 1.2.0

### 🎬 Vimeus (`vimeus.com`)
- **Estado:** ✅ Funcional
- **Contenido:** Películas, Series y Anime
- **Idioma:** Español Latino
- **Resolvers propios:** VOE, GoodStream, Vimeos, VidHide/Do7Go/DS2Play, StreamWish/HlsWish, OkRu, Filemoon
- **Integración:** Embed directo vía API oficial de Vimeus (TMDB ID)
- **Versión:** 1.0.0

---

## 🚀 Cargar en Nuvio

Añade esta URL en **Nuvio → Settings → Plugins:**

```
https://raw.githubusercontent.com/Kokuuuuuun/Nuvio-Kdramas-Providers-Latino/main/manifest.json
```

---

## 🛠️ Resolvers Implementados

### DoramasFlix

| Servidor | Técnica | Estado |
|---|---|---|
| VOE | Decode específico (voeDecode) + base64 + loader JS | ✅ Funcional |
| StreamWish / FlasWish | Packed JS + extracción hls2/hls3/hls4 | ✅ Funcional |
| VidHide / Do7Go / DS2Play | Unpacker P,A,C,K,E,R | ✅ Funcional |
| OkRu | JSON parsing con ordenado por calidad | ✅ Funcional |
| Filemoon | Búsqueda directa m3u8 en HTML | ✅ Funcional |

### Vimeus

| Servidor | Técnica | Estado |
|---|---|---|
| VOE | Decode específico + permanentToken redirect + loader JS | ✅ Funcional |
| GoodStream | JWPlayer file extractor directo | ✅ Funcional |
| Vimeos | Eval packer 343 símbolos + JWPlayer m3u8 | ✅ Funcional |
| VidHide / DS2Play / Do7Go | Unpacker P,A,C,K,E,R | ✅ Funcional |
| OkRu | JSON parsing multi-calidad | ✅ Funcional |
| Filemoon | Eval packer + búsqueda m3u8 | ✅ Funcional |
| HlsWish / StreamWish | Packed JS + hls extraction | ⚠️ Cloudflare 403 (requiere JS) |
| Diasfem | - | ⚠️ Fingerprint JS (requiere navegador) |

---

## 📁 Estructura del Proyecto

```
src/
├── doramasflix/         # Provider DoramasFlix
│   ├── index.js         # Punto de entrada: getStreams()
│   ├── extractor.js     # Búsqueda por nombre y extracción de embeds
│   ├── resolvers.js     # Resolvers de video (VOE, VidHide, etc.)
│   └── http.js          # Utilidades fetch
└── vimeus/              # Provider Vimeus
    ├── index.js         # Punto de entrada: getStreams()
    ├── extractor.js     # Fetch embed vía API Vimeus (TMDB ID)
    ├── resolvers.js     # Resolvers propios independientes
    └── http.js          # Utilidades fetch

providers/
├── doramasflix.js       # Bundle generado (esbuild)
└── vimeus.js            # Bundle generado (esbuild)

manifest.json            # Registro de providers para Nuvio
build.js                 # Script de build (esbuild)
worker.js                # Cloudflare Worker proxy para DoramasFlix API
test-vimeus.js           # Script de test para el provider Vimeus
```

---

## 🧪 Testing

```bash
# Test Vimeus - Película (Fight Club, TMDB 550)
node test-vimeus.js movie 550

# Test Vimeus - Serie (Game of Thrones S1E1, TMDB 1399)
node test-vimeus.js tv 1399 1 1

# Test Vimeus - Anime (Attack on Titan S1E1, TMDB 46261)
node test-vimeus.js tv 46261 1 1
```

---

## 🔨 Build

```bash
# Construir todos los providers
node build.js

# Construir solo un provider específico
node build.js vimeus
node build.js doramasflix
```

---

## 📝 Notas Técnicas

- Usa `fetch` nativo — compatible con **Nuvio/Hermes** (React Native)
- **No requiere** `axios`, `node-fetch` ni dependencias externas en runtime
- Los providers Vimeus y DoramasFlix tienen sus propios `resolvers.js` **independientes** (sin código compartido)
- Build system basado en **esbuild** — transpila async/await a generators (Hermes compatible)
- Cloudflare Worker incluido como proxy para la API GraphQL de DoramasFlix
- La integración Vimeus usa la **API oficial de embed** con `view_key` + TMDB ID

---

## 🗺️ Roadmap

- [ ] **DoramasVIP** — Implementar provider
- [ ] **DoramasMP4** — Implementar provider MP4
- [ ] **Mejorar Filemoon** — Resolver con AES-GCM para Vimeus
- [ ] **HlsWish** — Resolver con bypass Cloudflare
- [ ] **Testing automático** — CI/CD con GitHub Actions
