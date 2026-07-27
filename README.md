# build-transformer-engine-cu12

Pre-built CUDA 12 core wheels for
[NVIDIA Transformer Engine](https://github.com/NVIDIA/TransformerEngine), across
Python versions and CPU architectures.

## Installation

Following the PyTorch convention, artifacts are published to a separate index
for each CUDA version. The CUDA 12 core is independent of the Python and
PyTorch version: one architecture-specific wheel is shared across the
compatible `cu121`, `cu124`, `cu126`, `cu128`, `cu129` indexes.

Once released, pre-built wheels will be available on
[Astral's GPU indexes](https://wheels.astral.sh/index.html).
For example, to install the Transformer Engine PyTorch extension and its
patched CUDA 12 core:

```console
$ uv add 'transformer-engine[pytorch]' --index astral-cu128=https://wheels.astral.sh/simple/cu128/
```

This configures the index and uses it as the source for the metapackage,
CUDA 12 core, and PyTorch extension:

```toml
[tool.uv.sources]
transformer-engine = { index = "astral-cu128" }
transformer-engine-cu12 = { index = "astral-cu128" }
transformer-engine-torch = { index = "astral-cu128" }

[[tool.uv.index]]
name = "astral-cu128"
url = "https://wheels.astral.sh/simple/cu128/"
```

Or, with `uv pip`:

```console
$ uv pip install --index https://wheels.astral.sh/simple/cu128/ 'transformer-engine[pytorch]'
```

The core and metapackage apply the same compatibility patch, so either
installation order retains support for locally versioned PyTorch extension
wheels.

## Supported versions

Wheels can be built for the following NVIDIA Transformer Engine versions:

- [`2.16.0`](https://github.com/NVIDIA/TransformerEngine/releases/tag/v2.16)
- [`2.15.0`](https://github.com/NVIDIA/TransformerEngine/releases/tag/v2.15)
- [`2.14.0`](https://github.com/NVIDIA/TransformerEngine/releases/tag/v2.14)
- [`2.13.0`](https://github.com/NVIDIA/TransformerEngine/releases/tag/v2.13)
- [`2.12.0`](https://github.com/NVIDIA/TransformerEngine/releases/tag/v2.12)
- [`2.11.0`](https://github.com/NVIDIA/TransformerEngine/releases/tag/v2.11)
- [`2.10.0`](https://github.com/NVIDIA/TransformerEngine/releases/tag/v2.10)
- [`2.9.0`](https://github.com/NVIDIA/TransformerEngine/releases/tag/v2.9)
- [`2.8.0`](https://github.com/NVIDIA/TransformerEngine/releases/tag/v2.8)
- [`2.7.0`](https://github.com/NVIDIA/TransformerEngine/releases/tag/v2.7)
- [`2.6.0`](https://github.com/NVIDIA/TransformerEngine/releases/tag/v2.6)
- [`2.5.0`](https://github.com/NVIDIA/TransformerEngine/releases/tag/v2.5)
- [`2.4.0`](https://github.com/NVIDIA/TransformerEngine/releases/tag/v2.4)
- [`2.3.0`](https://github.com/NVIDIA/TransformerEngine/releases/tag/v2.3)
- [`2.2.1`](https://github.com/NVIDIA/TransformerEngine/releases/tag/v2.2.1)

The native CUDA core is built once per CPU architecture and CUDA major
version. CUDA 12 wheels are Python-version-independent and use NVIDIA's
upstream CUDA 12.3 toolchain.

## License

build-transformer-engine-cu12 is licensed under the
[Apache License, Version 2.0](LICENSE).

<div align="center">
  <a target="_blank" href="https://astral.sh" style="background:none">
    <img src="https://raw.githubusercontent.com/astral-sh/ruff/main/assets/svg/Astral.svg" alt="Made by Astral">
  </a>
</div>
