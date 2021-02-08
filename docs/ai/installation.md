---
title: 安裝 AI 工具
description: 描述如何安裝適用於 Visual Studio 的 AI 工具
keywords: AI, Visual Studio
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: cdbabcc9288a2f878b4c8cd86dbba97922f471c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841441"
---
# <a name="installation"></a>安裝

Visual Studio Tools for AI 可以安裝在 Windows 64 位元作業系統上。

## <a name="install-visual-studio-tools-for-ai"></a>安裝 Visual Studio Tools for AI

此延伸模組適用於 Visual Studio 2015 和 Visual Studio 2017 Community 版或更高版本。

您可以從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.vstoolsai-vs2017) 或從 Visual Studio 內下載這些工具：

1. 選取 [**工具**  >  **擴充功能和更新**]。

   ![Visual Studio 中的 [擴充功能和更新] 功能表](media/installation/extensions.png)

2. 在 [擴充功能和更新] 對話方塊中，選取左側的 [線上]。
3. 在右上角的 [搜尋] 方塊中，鍵入或輸入 "tools for ai"。
4. 從結果中選取 [Visual Studio Tools for AI]。
5. 選取 [下載]。

## <a name="prepare-your-local-machine"></a>準備本機電腦
在本機電腦上為深度學習模型定型之前，請確定您已安裝適用的先決條件。 這包括確定您的 NVIDIA GPU (如果有的話) 有最新的驅動程式與程式庫。 此外，請確定您已安裝 Python 和 Python 程式庫 (例如 NumPy、SciPy)，以及您打算在專案中使用的適當深度學習架構，例如 Microsoft Cognitive Toolkit (CNTK)、TensorFlow、Caffe2、MXNet、Keras、Theano、PyTorch 與 Chainer。

> [!NOTE]
> 以下各小節中的軟體簡介摘錄自其首頁。

### <a name="nvidia-gpu-driver"></a>NVIDIA GPU 驅動程式

深度學習架構利用 NVIDIA GPU 讓電腦以近似真正人工智慧的速度、正確性和規模進行學習。 如果您的電腦有 NVIDIA GPU 卡，請參閱 [NVIDIA 驅動程式下載](https://www.nvidia.com/Download/index.aspx)或嘗試進行作業系統更新，以安裝最新的驅動程式。

### <a name="cuda"></a>CUDA

[CUDA](https://developer.nvidia.com/cuda-zone) 是 NVIDIA 首創的平行運算平台和程式設計模型。 它充分利用 GPU 的強大功能，來大幅提升運算效能。 目前，深度學習架構需要 CUDA Toolkit 8.0。

安裝 CUDA

- 造訪此[網站](https://developer.nvidia.com/cuda-80-ga2-download-archive) \(英文\)，下載 CUDA 並加以安裝。
- 請務必安裝 CUDA 執行階段程式庫，然後將 CUDA 二進位檔路徑新增至 %PATH% 或 $Path 環境變數。
- 在 Windows 上，這個路徑預設為 "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin"。

![在 Windows 上安裝 CUDA](media/installation/install_cuda_win.png)

### <a name="cudnn"></a>cuDNN

[cuDNN](https://developer.nvidia.com/cudnn) (CUDA 深度類神經網路程式庫) 是由 NVIDIA 提供之深度類神經網路基本功能的 GPU 高速程式庫。 最新的深度學習架構需要 cuDNN v6。

安裝 cuDNN：

- 前往 [NVIDIA 開發人員](https://developer.nvidia.com/rdp/cudnn-download)以下載並安裝最新套件。
- 確定將包含 cuDNN 二進位檔的目錄新增至 %PATH% 或 $Path 環境變數。
- 在 Windows 上，您可以將 cudnn64_6.dll 複製到 "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin"。

> [!NOTE]
> 舊版的深度學習架構 (例如 CNTK 2.0 和 TensorFlow 1.2.1) 需要 cuDNN v5.1。 不過，您可以同時安裝多個 cuDNN 版本。

### <a name="python"></a>Python

Python 一直是深度學習應用程式的主要程式設計語言。 需要 **64 位元** Python 版本，建議使用 [Python 3.5.4](https://www.python.org/downloads/release/python-354/) 以取得最佳相容性。

### <a name="to-install-python-on-windows"></a>在 Windows 上安裝 Python

- 建議安裝的 Python 啟動器僅供您自己使用，並將 Python 新增至 %PATH% 環境變數。
- 確定安裝 pip，這是套件管理系統，可安裝及管理以 Python 撰寫的軟體套件。

深度學習架構需要 pip 才能進行安裝。

![在 Windows 上安裝 Python](media/installation/install_python_win.png)

然後，我們需要確認是否已正確安裝 Python 3.5，並藉由在終端機中執行下列命令，來將 pip 升級為最新版本：

- **Windows**

  ```cmd
  C:\Users\test>python -V
  Python 3.5.4

  C:\Users\test>pip3.5 -V
  pip 9.0.1 from c:\users\test\appdata\local\programs\python\python35\lib\site-packages (python 3.5)

  C:\Users\test>python -m pip install -U pip
  ```

- **macOS**

  ```bash
  MyMac:~ test$ python3.5 -V
  Python 3.5.4

  MyMac:~ test$ pip3.5 -V
  pip 9.0.1 from /Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages (python 3.5)

  MyMac:~ test$ python3.5 -m pip install -U pip
  ```

### <a name="python-on-visual-studio"></a>Visual Studio 上的 Python

Visual Studio 透過延伸模組來完全支援 Python。
如需詳細資訊，請深入了解如何安裝[適用於 Visual Studio 的 Python 工具](../python/installing-python-support-in-visual-studio.md)。

### <a name="numpy-and-scipy"></a>NumPy 和 SciPy

- **NumPy** 是一般目的陣列處理套件，其設計目的是為了有效率地操作任意記錄的大型多維陣列，但針對小型多維陣列卻不用犧牲太多速度。

- **SciPy** (唸成 "Sigh Pie") 是相依於 NumPy 之數學、科學和工程的開放原始碼軟體。 從 1.0.0 版開始，SciPy 現在會有適用於 Windows 之官方預先建置的 wheel 套件。

若要安裝 NumPy 和 SciPy，請在終端機中執行下列命令：

```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
> 上述命令會將現有舊的或非官方 (例如來自 http://www.lfd.uci.edu/~gohlke/pythonlibs/ 之適用於 Windows 的第三方套件) NumPy 和 SciPy 升級為最新官方版本。

### <a name="microsoft-cognitive-toolkit-cntk"></a>Microsoft Cognitive Toolkit (CNTK)

[Microsoft Cognitive Toolkit](https://cntk.ai) 是整合深度學習工具組，透過導向式圖表以一系列計算步驟來描述類神經網路。 CNTK 支援 Python 和 BrainScript 程式設計語言。

> [!NOTE]
> CNTK 目前不支援 macOS。

若要安裝 CNTK Python 套件，請參閱[如何安裝 CNTK](/cognitive-toolkit/Setup-CNTK-on-your-machine) \(英文\)。

### <a name="tensorflow"></a>TensorFlow

[TensorFlow](https://www.tensorflow.org/) \(英文\) 是使用資料流程圖表進行數值計算的開放原始碼軟體程式庫。 如需詳細的安裝說明，請參閱[這裡](https://www.tensorflow.org/install/)。

> [!NOTE]
> 從 1.2 版開始，TensorFlow 不再為 macOS 提供 GPU 支援。

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/) 是輕量型、模組化且可調整規模的深度學習架構。 Caffe2 建置在原始 Caffe 上，並以運算式、速度和模組化為設計考量。

目前，沒有預先建置的 Caffe2 python wheel 套件可用。

請前往[這裡](https://caffe2.ai/docs/getting-started.html)以從原始程式碼建置。

### <a name="mxnet"></a>MXNet

[Apache MXNet (籌備中)](https://mxnet.incubator.apache.org/) 是專為效率和彈性所設計的深度學習架構。 它可讓您 **混合** [符號和命令式程式設計](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts)以提高效率和生產力。

若要安裝 MXNet，請在終端機中執行下列命令：

- 使用 GPU

  ```bash
  pip3.5 install mxnet-cu80==0.12.0
  ```

- 不使用 GPU

  ```bash
  pip3.5 install mxnet==0.12.0
  ```

### <a name="keras"></a>Keras

[Keras](https://keras.io/) \(英文\) 是以 Python 撰寫，能夠在 CNTK、TensorFlow 或 Theano 上執行的高階類神經網路 API。 其開發重點在於加快試驗速度。 能夠盡可能以最低延遲來實現構想是進行理想研究的關鍵。

若要安裝 Keras，請在終端機中執行下列命令：

```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

[Theano](http://deeplearning.net/software/theano/) 是 Python 程式庫，可讓您有效率地定義、最佳化及評估涉及多維陣列的數學運算式。

若要安裝 Theano，請在終端機中執行下列命令：

```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[PyTorch](https://pytorch.org/) 是 python 套件，提供兩項高階功能：

- 使用強式 GPU 加速的 Tensor 計算 (例如 numpy)
- 建置在磁帶型 autograd 系統上的深度類神經網路

若要安裝 PyTorch，請在終端機中執行下列命令：

- **Windows**

  目前沒有官方 wheel 套件。 您可以從 [Anaconda](https://anaconda.org/pytorch/repo?type=all) 或 [University of California](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pytorch) 下載協力廠商套件。

  - 將其解壓縮到您的主目錄，例如 *C:\Users\test\pytorch*。
  - 將 *C:\Users\test\pytorch\Lib\site-packages* 新增至 %PYTHONPATH% 環境變數。

    ```bash
    pip3 install http://download.pytorch.org/whl/cu80/torch-0.4.0-cp36-cp36m-win_amd64.whl
    pip3 install torchvision
    ```

- **macOS**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
  ```

  > [!NOTE]
  > macOS 二進位檔不支援 CUDA；如果需要 CUDA，請從來源進行安裝

- **Linux**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
  ```

  > [!NOTE]
  > 此單一套件支援 GPU 和 CPU。

最後，在非 Windows 上安裝 torchvision：

```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>Chainer

[Chainer](https://chainer.org/) 是以彈性為目標的 Python 深度學習架構。 它提供以 define-by-run 方法為基礎的自動區分 API (也稱為動態計算圖表)，以及物件導向的高階 API 來建置及定型類神經網路。

若要啟用 CUDA 支援，請安裝 [CuPy](https://github.com/cupy/cupy)：

```bash
pip3.5 install cupy
```

> [!NOTE]
> 在 Windows 上，您需要 2015 版的 [Visual Studio](https://visualstudio.microsoft.com/) 或 [Microsoft Visual C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/)，才能使用 CUDA 8.0 編譯 CuPy。

若要安裝 Chainer，請在終端機中執行下列命令：

```bash
pip3.5 install chainer==3.0.0
```
