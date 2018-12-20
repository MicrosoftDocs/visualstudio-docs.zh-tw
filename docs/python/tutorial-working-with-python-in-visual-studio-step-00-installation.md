---
title: Visual Studio 中的 Python 教學課程步驟 0，安裝
titleSuffix: ''
description: 在 Visual Studio 中 Python 核心逐步解說的步驟 0 (安裝必要條件)。
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5096d0789f8f3c84c041591918af73cc230fe16d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064439"
---
# <a name="install-python-support-in-visual-studio"></a>在 Visual Studio 中安裝 Python 支援

> [!Note]
> 目前在 Visual Studio for Windows 中沒有 Python 支援；但在 Mac 和 Linux 上，Python 支援可透過 [Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial) 取得。

1. 下載並執行適用於 Windows 的最新版 Visual Studio 2017 安裝程式 (Python 支援存在於 15.2 版和更新版本)。 如果您已經安裝 Visual Studio，請執行 Visual Studio 安裝程式並移至步驟 2。

    > [!div class="nextstepaction"]
    > [安裝 Visual Studio 2017 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Community Edition 是針對個別開發人員、課堂學習、學術研究和開放原始碼開發。 針對其他用途，請安裝 [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) 或 [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)。

1. 安裝程式會顯示一份工作負載清單，而工作負載是特定開發區域的相關選項群組。 針對 Python，選取 [Python 開發] 工作負載，並選取 [安裝]：

    ![Visual Studio 安裝程式中的 Python 開發工作負載](media/installation-python-workload.png)

1. 若要快速測試 Python 支援，請啟動 Visual Studio，按 **Alt**+**I** 以開啟 Python **互動式**視窗，然後輸入 `2+2`。 如果您沒有看到 **4** 的輸出，請重新檢查您的步驟。

    ![在互動式視窗中測試 Python](media/installation-interactive-test.png)

## <a name="next-step"></a>後續步驟

> [!div class="nextstepaction"]
> [步驟 1：建立 Python 專案](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>另請參閱

- [手動識別現有的 Python 解譯器](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [在 Visual Studio 2015 和更早版本中安裝 Python 支援](installing-python-support-in-visual-studio.md)
- [安裝位置](installing-python-support-in-visual-studio.md#install-locations)
