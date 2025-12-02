# demucs-cxfreeze (with diffq support)

Fork with `diffq` support for quantized models (mdx_q, mdx_extra_q, htdemucs_mmi).

## Freezing `demucs`

**With CUDA support (Windows & Linux)**
```
pip3 install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu126 demucs SoundFile cx-Freeze diffq
```

**CPU only (Any OS)**
```
pip3 install torch torchvision torchaudio demucs SoundFile cx-Freeze diffq
```

And then:
```
cxfreeze main.py --target-dir=dist --target-name=demucs-cxfreeze --packages=torch --includes=demucs.htdemucs,diffq
```

Copy `venv/Lib/site-packages/_soundfile_data` to `dist/lib/_soundfile_data`

## Supported Models

With `diffq` included, these additional models are now supported:
- `mdx_q` - MDX Quantized (faster)
- `mdx_extra_q` - MDX Extra Quantized (best balance speed/quality)
- `htdemucs_mmi` - HTDemucs with more musical information

## Additional Dependencies (should be shipped with frozen Demucs)

### `ffmpeg` and `ffprobe`

The directory containing `ffmpeg` and `ffprobe` binaries should be added to the `PATH` environment variable.

#### Windows
https://www.gyan.dev/ffmpeg/builds/ffmpeg-release-essentials.zip

#### macOS
- https://evermeet.cx/ffmpeg/ffmpeg-109428-g10a56363a7.zip
- https://evermeet.cx/ffmpeg/ffprobe-109428-g10a56363a7.zip

### Models

Downloaded models and their YAML files should be placed in a directory passed via the `--repo` argument, 
or in the `DEMUCS_CACHE_DIR` environment variable path.

#### All model files list
https://raw.githubusercontent.com/facebookresearch/demucs/main/demucs/remote/files.txt
