# MixelNodes · media

Vídeos y archivos pesados de [mixelnodes.com](https://mixelnodes.com). No se despliegan desde aquí:
la web los enlaza a través de la CDN gratuita de jsDelivr, solo cuando alguien pulsa reproducir.

```
https://cdn.jsdelivr.net/gh/MixelNodesHosting/media@a28aa3316b0785fca00f4559603e8ae86a32a357/videos/mixelshield-1080p.mp4
https://cdn.jsdelivr.net/gh/MixelNodesHosting/media@a28aa3316b0785fca00f4559603e8ae86a32a357/videos/mixelshield-720p.mp4
https://cdn.jsdelivr.net/gh/MixelNodesHosting/media@a28aa3316b0785fca00f4559603e8ae86a32a357/videos/mixelai-1080p.mp4
https://cdn.jsdelivr.net/gh/MixelNodesHosting/media@a28aa3316b0785fca00f4559603e8ae86a32a357/videos/mixelai-720p.mp4
```

- El repo tiene que ser **público** (jsDelivr no sirve repos privados).
- jsDelivr no sirve archivos de más de 20 MB: recomprime antes de subir (ver abajo).
- La web apunta a un commit concreto de este repo. Para cambiar un vídeo sin romper cachés: súbelo y copia el hash del nuevo commit (o crea un tag)
  y pon ese hash en lugar del actual en `src/config/media.js` de la web (o en la variable `VITE_MEDIA_BASE_URL`).

## Cómo se recomprimen

```bash
ffmpeg -i original.mp4 -vf scale=-2:1080 -c:v libx264 -preset slow -crf 27 -profile:v high \
  -pix_fmt yuv420p -movflags +faststart -c:a aac -b:a 96k -ac 2 nombre-1080p.mp4
ffmpeg -i original.mp4 -vf scale=-2:720 -c:v libx264 -preset slow -crf 27 -profile:v high \
  -pix_fmt yuv420p -movflags +faststart -c:a aac -b:a 96k -ac 2 nombre-720p.mp4
```
