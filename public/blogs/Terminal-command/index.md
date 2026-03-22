## 1. 使用 pip 安装 Python 包

使用清华源加速安装：

```bash
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple 包名
```
将 包名 替换为你需要安装的 Python 包名称。

## 2. 使用 conda 创建虚拟环境
- **方式一：** 按名称创建虚拟环境
```bash
conda create -n 环境名 python=3.8
conda activate 环境名
conda deactivate
```
建议 Python 版本使用 3.8 或 3.9
- **方式二：** 指定路径创建虚拟环境
```bash
conda create --prefix ./biot python=3.8
conda activate ./biot
如果虚拟环境在自定义路径，例如 D:\python-code\biot，可以使用：
conda activate D:\python-code\biot
```

## 3. 安装 PyTorch

- **GPU 版本（以 CUDA 11.8 为例）**
```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
```
- **CPU 版本**
```bash
pip install torch torchvision torchaudio
```

根据电脑硬件选择 CPU 或 GPU 版本。

## 4. 清理 pip 缓存
```bash
pip cache purge
```

清理安装过程中生成的缓存文件，释放空间。