# Real-ESRGAN Web 界面

基于 Gradio 库的 [Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN) 浏览器界面。

![](https://chatgpt.com/c/screenshot.png)

# 依赖与安装

- Python >= 3.7（推荐使用 [Anaconda](https://www.anaconda.com/download/#linux) 或 [Miniconda](https://docs.conda.io/en/latest/miniconda.html)）
- [PyTorch >= 1.7](https://pytorch.org/)

## 安装步骤

1. 克隆仓库

```sh
git clone https://github.com/coderxi1/Real-ESRGAN-webui.git --recurse-submodules
cd Real-ESRGAN-webui
```

2. 安装依赖包

```sh
# 如果使用 conda
# conda create -n real-esrgan-webui python=3.10.9
# conda activate real-esrgan-webui

pip install basicsr
pip install facexlib
pip install gfpgan

cd Real-ESRGAN # 进入 Real-ESRGAN 子模块进行设置

pip install -r requirements.txt
python setup.py develop
```

3. 启动 Web 界面

```sh
cd .. # 返回到 webui 目录

pip install gradio
python webui.py
```

## 注意事项

如果遇到以下错误，请检查您的 torch 是否为 CPU 版本。

```javascript
ValueError: Number of processes must be at least 1

Error "slow_conv2d_cpu" not implemented for 'Half'
```

您可以运行以下 Python 代码检查 torch 版本：

```go
import torch
print(torch.__version__)
```

如果版本字符串中包含 `+cpu`，例如 `2.0.0+cpu`，这意味着您安装的是 CPU 版本的 torch。请访问 [pytorch.org](https://pytorch.org/get-started/locally/) 安装适合的版本。

- 如果您通过 `pip` 安装，请确保先卸载已安装的版本：

```sh
# pip uninstall cpuonly (如已安装)
pip uninstall torch torchvision torchaudio
```

然后重新安装新版本。

- 如果您通过 `conda` 安装，可能会遇到以下错误：

```javascript
ImportError: cannot import name 'COMMON_SAFE_ASCII_CHARACTERS' from 'charset_normalizer.constant'
```

通过安装较低版本的 `charset-normalizer` 来解决：

```sh
pip install charset-normalizer==2.1.0
```

## API

使用 `--api` 参数，然后访问 `/docs` 查看文档。