---
title: "選取並安裝 Python 解譯器 | Microsoft Docs"
description: "Visual Studio 中所支援 Python 解譯器的完整清單，其中包含在何處找到其安裝程式的簡要說明。"
ms.custom: 
ms.date: 02/20/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 1bdec69c45cbd6ebb7943ce38853fd2207000a0f
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="installing-python-interpreters"></a>安裝 Python 解譯器

根據預設，在 Visual Studio 2017 中安裝 Python 開發工作負載，也會安裝 Python 3 (64 位元)。 如[安裝](installing-python-support-in-visual-studio.md)中所述，您可以選擇安裝 32 位元和 64 位元版本的 Python 2、Python 3、Anaconda 2 和 Anaconda 3。

您也可以手動安裝下表所列出 Visual Studio 安裝程式以外的任何解譯器。 例如，如果您在安裝 Visual Studio 前已經安裝了 Anaconda 3，就不需透過 Visual Studio 安裝程式再次安裝。

針對 Visual Studio 2015 及更早版本，您必須安裝其中一個解譯器。

Visual Studio (所有版本) 會檢查登錄 (依照 [PEP 514 - Windows 登錄中的 Python 註冊](https://www.python.org/dev/peps/pep-0514/) \(英文\))，以自動偵測每個安裝的 Python 解譯器與其環境。

如果 Visual Studio 偵測不到安裝的環境，請參閱[手動識別現有的環境](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment)。

Visual Studio 會在 [Python 環境](managing-python-environments-in-visual-studio.md) 視窗中顯示所有已知的環境，並自動偵測現有解譯器的更新。

| 解譯器 | 描述 |
| --- | --- |
| [CPython](https://www.python.org/) | 這是「原生」且最常用的解譯器，提供 32 位元和 64 位元版本 (建議使用 32 位元)。 包含最新的語言功能、最大的 Python 套件相容性、完整的偵錯支援，以及與 [IPython](http://ipython.org/) 的互通性。 另請參閱：[Should I use Python 2 or Python 3?](http://wiki.python.org/moin/Python2orPython3) (我應該使用 Python 2 還是 Python 3？) 請注意，Visual Studio 2015 及更早版本不支援 Python 3.6，因此可能會出現「不支援 python 3.6 版」的錯誤。 請改用 Python 3.5 或更早版本。 |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Python 的 .NET 實作具有 32 位元和 64 位元版本，除了提供 C#/F#/Visual Basic 互通性之外，還可存取 .NET API、標準 Python 偵錯 (但不包括 C++ 混合模式偵錯) 及混合式 IronPython/C# 偵錯。 不過，IronPython 並不支援虛擬環境。 |
| [Anaconda](https://www.continuum.io) | 由 Python 提供技術支援的開放式資料科學平台，它包含最新版的 CPython 和大多數難以安裝的套件。 如果您無法決定要使用哪一個解譯器，建議您使用此解譯器。 |
| [PyPy](http://www.pypy.org/) | Python 的高效能追蹤 JIT 實作，適合用來處理長時間執行的程式，以及您找出效能問題但找不到其他解決方案的情況。 可以與 Visual Studio 搭配運作，但對進階偵錯功能的支援有限。 |
| [Jython](http://www.jython.org/) | 「Java 虛擬機器」(JVM) 上的 Python 實作。 與 IronPython 類似，在 Jython 中執行的程式碼可以與 Java 類別和程式庫進行互動，但可能無法使用許多適用於 CPython 的程式庫。 可以與 Visual Studio 搭配運作，但對進階偵錯功能的支援有限。 |

開發人員如果想要為 Python 環境提供新形式的偵測，可以參閱 [PTVS 環境偵測 (英文)](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (github.com)。

## <a name="moving-an-interpreter"></a>移動解譯器

如果您使用檔案系統將現有的解譯器移至新的位置，則 Visual Studio 不會自動偵測變更。

- 如果您原本透過 [Python 環境] 視窗指定解譯器的位置，請使用該視窗中的 [設定] 索引標籤來編輯其環境，以便識別新的位置。 請參閱[手動識別現有的環境](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment)。

- 如果您已使用安裝程式安裝解譯器，則請使用下列步驟在新的位置中重新安裝解譯器：

  1. 將 Python 解譯器還原到其原始位置。
  2. 使用其安裝程式將它解除安裝，並一併清除登錄項目。
  3. 在所需的位置重新安裝解譯器。
  4. 重新啟動 Visual Studio，如此應該會自動偵測新的位置來取代舊的位置。

遵循此程序可確保識別解譯器位置 (由 Visual Studio 所使用) 的登錄項目已適當更新。 使用安裝程式也可以處理任何可能存在的其他副作用。

## <a name="see-also"></a>另請參閱

- [管理 Python 環境](managing-python-environments-in-visual-studio.md)
- [選取專案的解譯器](selecting-a-python-environment-for-a-project.md)
- [將 requirements.txt 用於相依性](managing-required-packages-with-requirements-txt.md)
- [搜尋路徑](search-paths.md)
- [Python 環境視窗參考](python-environments-window-tab-reference.md)