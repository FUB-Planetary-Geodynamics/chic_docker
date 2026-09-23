# CHIC Docker Image

This repository provides a Docker image for running CHIC.

The image is hosted on GitHub Container Registry:

```text
ghcr.io/fub-planetary-geodynamics/chic_docker:v2_23_sep_2026-amd64
```

## Requirements

Install Docker first:

- Docker Desktop for macOS or Windows
- Docker Engine for Linux

## Pull the image

```bash
docker pull --platform linux/amd64 ghcr.io/fub-planetary-geodynamics/chic_docker:v2_23_sep_2026-amd64
```

## Run CHIC

CHIC expects an input file named `input.txt` inside the working directory.

Place your `input.txt` file in your current directory and run:

```bash
docker run --rm --platform linux/amd64 \
  -v "$(pwd):/work" \
  -w /work \
  ghcr.io/fub-planetary-geodynamics/chic_docker:v2_23_sep_2026-amd64
```

Output files written by CHIC will appear in the same local directory.

## Run with a differently named input file

If your local input file has another name, for example `input_2`, mount it as `input.txt` inside the container:

```bash
docker run --rm --platform linux/amd64 \
  -v "$(pwd):/work" \
  -v "$(pwd)/input_2:/work/input.txt:ro" \
  -w /work \
  ghcr.io/fub-planetary-geodynamics/chic_docker:v2_23_sep_2026-amd64
```

## Windows PowerShell

If you are using Windows PowerShell, use:

```powershell
docker pull --platform linux/amd64 ghcr.io/fub-planetary-geodynamics/chic_docker:v2_23_sep_2026-amd64
```

Run with an `input.txt` file in the current folder:

```powershell
docker run --rm --platform linux/amd64 `
  -v "${PWD.Path}:/work" `
  -w /work `
  ghcr.io/fub-planetary-geodynamics/chic_docker:v2_23_sep_2026-amd64
```

Run with a differently named input file, for example `input_2`:

```powershell
docker run --rm --platform linux/amd64 `
  -v "${PWD.Path}:/work" `
  -v "${PWD.Path}\input_2:/work/input.txt:ro" `
  -w /work `
  ghcr.io/fub-planetary-geodynamics/chic_docker:v2_23_sep_2026-amd64
```

## Notes

This image is built for `linux/amd64`.

On Apple Silicon Macs, such as M1, M2, M3, or M4, Docker runs this image via amd64 emulation. Therefore, keep the `--platform linux/amd64` option in the commands above.

On native Intel/AMD Linux systems, the `--platform linux/amd64` option is usually not required, but it is safe to keep it.
