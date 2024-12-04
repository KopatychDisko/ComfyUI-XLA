<div align="center">

# ComfyUI-TPU

**TPUs/XLA devices support for ComfyUI**

[![Dynamic JSON Badge][discord-shield]][discord-url]

<!-- Workaround to display total user from https://github.com/badges/shields/issues/4500#issuecomment-2060079995 -->

[discord-shield]: https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fdiscord.com%2Fapi%2Finvites%2Fisekaicreation%3Fwith_counts%3Dtrue&query=%24.approximate_member_count&logo=discord&logoColor=white&label=Discord&color=green&suffix=%20total
[discord-url]: https://discord.com/invite/isekaicreation

</div>

#### Updates

- 29/11/2024: Multi-TPUs/XLA devices support for ComfyUI! Might even work on GPUs!
- 26/11/2024: Initial ComfyUI Support for TPUs/XLA devices!

#### TPU/XLA Devices Mode

Users can enable by adding the command line arg `--xla`

```
python3.10 main.py --xla
```

To utilize all your devices with SPMD/FSDPv2, you can use the command line arg `--xla_spmd`

```
python3.10 main.py --xla_spmd
```

#### TPU/XLA Devices Requirements

### TPU

Users with TPU/XLA devices can install the PyTorch XLA stable build with the following command:

```
pip install torch~=2.5.0 torch_xla[tpu]~=2.5.0 -f https://storage.googleapis.com/libtpu-releases/index.html
```

This is the command to install the nightly 2.6.0 which might have some performance improvements:

```
pip3 install --pre torch torchvision --index-url https://download.pytorch.org/whl/nightly/cpu
pip install 'torch_xla[tpu] @ https://storage.googleapis.com/pytorch-xla-releases/wheels/tpuvm/torch_xla-2.6.0.dev-cp310-cp310-linux_x86_64.whl' -f https://storage.googleapis.com/libtpu-releases/index.html
```

### GPU Plugin

For users with GPU, you can install the GPU Plugin to use Pytorch/XLA

```
pip install torch~=2.5.0 torch_xla~=2.5.0 https://storage.googleapis.com/pytorch-xla-releases/wheels/cuda/12.1/torch_xla_cuda_plugin-2.5.0-py3-none-any.whl
```

### Memory Info

To get memory info for TPU devices, install the [tpu-info](https://github.com/AI-Hypercomputer/cloud-accelerator-diagnostics/tree/main/tpu_info) package with the following command:

```
pip install tpu-info
```

To monitor tpu-info

```
watch -n0 tpu-info
```

#### To-do list

- [x] Bare Minimum TPUs/XLA devices support
- [x] Install & Requirements Docs
- [x] Cache XLA HLO Graph
- [x] SPMD/FSDPv2 mode
- [ ] Optimize For ComfyUI
- [ ] Eager mode
