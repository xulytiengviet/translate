# Translate · CVNSS4.0 · Multilingual

Static GitHub Pages web app: https://xulytiengviet.github.io/translate/

## Features

- Vietnamese ⇄ CVNSS4.0 using the exact user-provided `CVNSSConverter` 5.0.0-audit-safe engine, including ambiguity-aware canonical decoding.
- Edit either side; both panes synchronize instantly on device.
- Select among 33 languages and sequentially generate multiple translations in the browser (results displayed side by side).
- No hosted inference backend, paid translation API, or server-side user text upload.
- AI translation is **experimental**: NLLB-200 distilled 600M via Transformers.js WASM; it is **not Hy-MT2**. Initial model downloads may exceed 1GB depending on weight files and browser cache. Not every device can run it reliably. Selected language translations are processed **sequentially**, not simultaneous GPU batch processing.
- Existing upstream Hy-MT2 reference, training materials and upstream license remain in this repository. The Hy-MT2 weights themselves are not used by this web app.

## Publish

Repo → Settings → Pages → Build and deployment → Deploy from a branch → `main` / `/(root)` → Save.

If the Pages URL returns 404, verify that GitHub Pages is enabled and deployment succeeded.

## Local smoke test

```bash
node -e "const c=require('./assets/cvnss-converter.js'); console.log(c.selfTest()); console.log(c.fromCqn('Tiếng Việt'));"
python -m http.server 8000
```

Open http://localhost:8000/ in a browser. A network connection is needed on first load for Transformers.js and NLLB weights; browser inference has no paid API. Some CDN hosting and model downloads are external static files, but inference is local. 

## Licensing

Check `LICENSE.txt` for Tencent Hy-MT2, and the upstream NLLB model's license and usage constraints before redistribution or commercial deployment. Preserve provenance of the contributed CVNSS engine. Do not assume all code/models are MIT licensed.
