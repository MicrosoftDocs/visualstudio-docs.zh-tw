---
title: 在本機定型 TensorFlow 模型
description: 在適用於 Visual Studio 的 AI 工具本機執行 TensorFlow 模型
keywords: AI, Visual Studio, TensorFlow, 本機
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 0ceb21701958630c8b783d5b6850c5e0a0ab229a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841376"
---
# <a name="train-a-tensorflow-model-locally"></a>在本機定型 TensorFlow 模型

在本快速入門中，我們在 Visual Studio Tools for AI 本機使用 [MNIST](http://yann.lecun.com/exdb/mnist/) 資料集來定型 TensorFlow 模型。

MNIST 資料庫具有 60,000 個範例的定型集，以及 10,000 個手寫數字範例的測試集。

## <a name="prerequisites"></a>必要條件

開始之前，請確定您已安裝下列項目：

### <a name="google-tensorflow"></a>Google TensorFlow

在終端機中執行下列命令：

```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>NumPy 和 SciPy
安裝 [NumPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) 和 [SciPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy)。

### <a name="download-sample-code"></a>下載範例程式碼
下載這個 [GitHub 存放庫](https://github.com/Microsoft/samples-for-ai)，其中包含在 TensorFlow、CNTK、Theano 等之間進行深度學習的使用者入門範例。

## <a name="open-solution-and-train-model"></a>開啟方案並定型模型

- 啟動 Visual Studio，然後選取 [檔案] > [開啟] > [專案/方案]。

- 從下載的範例存放庫中選取 **TensorFlow 範例** 資料夾，然後開啟 **TensorflowExamples.sln** 檔案。

   ![開啟專案](media/tensorflow-local/open-project.png)

   ![開啟方案](media/tensorflow-local/open-solution.png)

- 在 [方案總管] 中，找到 MNIST 專案並按一下滑鼠右鍵，然後選取 [設定為啟始專案]。

- 按一下 [啟動]。

- 輸出會列印於主控台中。

   ![主控台中的範例輸出](media/tensorflow-local/console-output.png)

> [!div class="nextstepaction"]
> [在雲端中定型 TensorFlow 模型](tensorflow-vm.md)
