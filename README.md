# demucs-cxfreeze (with diffq support)

A frozen (standalone) build of Facebook's Demucs audio source separation tool, with **diffq** support for quantized models.

## Credits

This project is based on:
- **[stemrollerapp/demucs-cxfreeze](https://github.com/stemrollerapp/demucs-cxfreeze)** - Original frozen Demucs binary project
- **[facebookresearch/demucs](https://github.com/facebookresearch/demucs)** - The original Demucs source separation library by Facebook Research

## What's New

This fork adds `diffq` support, enabling the following quantized models that weren't available in the original:
- `mdx_q` - MDX Quantized (faster, smaller)
- `mdx_extra_q` - MDX Extra Quantized (best balance of speed/quality)

## Available Builds

| Platform | File | Notes |
|----------|------|-------|
| macOS Intel | `demucs-cxfreeze-mac-intel.zip` | For Intel Macs |
| macOS ARM | `demucs-cxfreeze-mac-arm.zip` | For Apple Silicon (M1/M2/M3) |
| Windows CUDA | `demucs-cxfreeze-win-cuda.7z` | GPU accelerated |
| Windows CPU | `demucs-cxfreeze-win-cpu.zip` | CPU only |

## Building from Source

**With CUDA support (Windows & Linux)**
```
pip3 install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu126 demucs SoundFile cx-Freeze diffq 'numpy<2'
```

**CPU only (Any OS)**
```
pip3 install torch torchvision torchaudio demucs SoundFile cx-Freeze diffq 'numpy<2'
```

And then:
```
cxfreeze main.py --target-dir=dist --target-name=demucs-cxfreeze --packages=torch --includes=demucs.htdemucs,diffq
```

## Supported Models

All standard Demucs models are supported:
- `htdemucs` - Hybrid Transformer Demucs (fast)
- `htdemucs_ft` - Fine-tuned HTDemucs (best quality, bag of 4)
- `htdemucs_6s` - 6-stem separation (+ piano, guitar)
- `hdemucs_mmi` - Hybrid Demucs with more musical information
- `mdx` - MDX architecture
- `mdx_extra` - MDX Extra (bag of 4)
- `mdx_q` - MDX Quantized ✨ **NEW**
- `mdx_extra_q` - MDX Extra Quantized ✨ **NEW**

## Requirements

### FFmpeg

`ffmpeg` and `ffprobe` must be in your PATH or provided separately. They are NOT bundled with this release.

#### Windows
https://www.gyan.dev/ffmpeg/builds/ffmpeg-release-essentials.zip

#### macOS
- https://evermeet.cx/ffmpeg/

### Models

Models are downloaded automatically by Demucs, or you can set the `DEMUCS_CACHE_DIR` environment variable to a directory containing pre-downloaded models.

Model file list: https://raw.githubusercontent.com/facebookresearch/demucs/main/demucs/remote/files.txt

## License

This project follows the licenses of the original projects:
- Demucs: MIT License
- demucs-cxfreeze: MIT License
