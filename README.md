# build-transformer-engine-cu12

Pre-built CUDA 12 core wheels for
[NVIDIA Transformer Engine](https://github.com/NVIDIA/TransformerEngine), across
Python versions and CPU architectures.

## Installation

Following the PyTorch convention, artifacts are published to a separate index
for each CUDA version. Each architecture-specific CUDA 12 core wheel uses
the same CUDA and PyTorch local version as its corresponding metapackage and
PyTorch extension. For example,
`transformer_engine_cu12-2.16.0+cu.12.8.torch.2.10-py3-none-manylinux_2_28_x86_64.whl`
matches the CUDA 12.8, PyTorch 2.10 extension. Core wheels are shared across
Python versions.

Once released, pre-built wheels will be available on
[Astral's GPU indexes](https://wheels.astral.sh/index.html).
For example, to install the Transformer Engine PyTorch extension and its
matching CUDA 12 core:

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

The core, metapackage, and PyTorch extension share their complete version, so
NVIDIA's original version checks and Python files work without compatibility
patches regardless of installation order.

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

The native CUDA core is built once per CUDA version and CPU architecture. Each
build then produces a separately versioned wheel for every supported PyTorch
version, reusing the same compiled native libraries, prebuilt PyTorch CUDA
manylinux image, and build matrix.

## License

build-transformer-engine-cu12 is licensed under the
[Apache License, Version 2.0](LICENSE).

<div align="center">
  <a target="_blank" href="https://astral.sh" style="background:none">
    <img src="https://raw.githubusercontent.com/astral-sh/ruff/main/assets/svg/Astral.svg" alt="Made by Astral">
  </a>
</div>
