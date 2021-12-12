**Home**
- [Home](../index.md)
---

# Image Convertions

Convert an jpg or png to webp
```bash
cwebp file-to-convert.jpg -o output-file-name.webp
```

Converting a `webp` image to `jpg` or `png`
- Convert a single file

```bash
ffmpeg -i file.webp out.png
```

- Convert a multiple files

```bash
for x in ls *.webp; do  ffmpeg -i $x ${x%.webp}.jpg; done
```