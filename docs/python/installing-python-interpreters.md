---
title: 選取並安裝 Python 解譯器
description: Visual Studio 中所支援 Python 解譯器的完整清單，其中包含在何處找到其安裝程式的簡要說明。
ms.date: 06/05/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8070bb93a1dd76ad29832afae15d83788300ae7a
ms.sourcegitcommit: 925db7adb9cb554b081c7e727d09680d4863feed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2021
ms.locfileid: "107941106"
---
# <a name="install-python-interpreters"></a>安裝 Python 解譯器

根據預設，會在 Visual Studio 2017 中安裝 Python 開發工作負載，之後也會安裝 Python 3 (64 位元)。 如[安裝](installing-python-support-in-visual-studio.md)中所述，您可以選擇安裝 32 位元和 64 位元版本的 Python 2 與 Python 3，以及 Miniconda (Visual Studio 2019) 或 Anaconda 2/Anaconda 3 (Visual Studio 2017)。

::: moniker range=">=vs-2019"
或者，可以從 [新增環境] 對話方塊安裝標準 Python 解譯器。 在 [Python 環境] 視窗或 Python 工具列中選取 [新增環境] 命令，選取 [Python 安裝] 索引標籤，指出要安裝哪一個解譯器，然後選取 [安裝]。
::: moniker-end

您也可以手動安裝下表所列出 Visual Studio 安裝程式以外的任何解譯器。 例如，如果您在安裝 Visual Studio 前已經安裝了 Anaconda 3，就不需透過 Visual Studio 安裝程式再次安裝。 如果可用的新版本未出現在 Visual Studio 安裝程式中，您也可以手動安裝解譯器。

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio 支援 Python 2.7 版以及3.5 版至3.7。 雖然您可能可以使用 Visual Studio 來編輯以其他 Python 版本所撰寫的程式碼，那些版本並非正式支援的版本，因此 IntelliSense 和偵錯之類的功能可能會無法運作。
::: moniker-end

針對 **Visual Studio 2015 及更早版本**，您必須手動安裝其中一個解譯器。

Visual Studio (所有版本) 會根據 [PEP 514 - Python registration in the Windows registry](https://www.python.org/dev/peps/pep-0514/) (PEP 514 - Windows 登錄中的 Python 註冊) 檢查登錄，以自動偵測每個安裝的 Python 解譯器與其環境。 Python 安裝通常位於 **HKEY_LOCAL_MACHINE\SOFTWARE\Python** (32 位元) 和 **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** (64 位元) 下如 **PythonCore** (CPython) 和 **ContinuumAnalytics** (Anaconda) 等要散發的節點內。

如果 Visual Studio 偵測不到安裝的環境，請參閱[手動識別現有的環境](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)。

Visual Studio 會在 [ [**Python 環境**](managing-python-environments-in-visual-studio.md#the-python-environments-window) ] 視窗中顯示所有已知的環境，並自動偵測現有解譯器的更新。

| 解譯器 | Description |
| --- | --- |
| [CPython](https://www.python.org/) | 這是「原生」且最常用的解譯器，提供 32 位元和 64 位元版本 (建議使用 32 位元)。 包含最新的語言功能、最大的 Python 套件相容性、完整的偵錯支援，以及與 [IPython](https://ipython.org/) 的互通性。 另請參閱： [我應該使用 python 2 還是 python 3？](https://wiki.python.org/moin/Python2orPython3)。 請注意，Visual Studio 2015 及更舊版本不支援 Python 3.6+，因此可能會出現 **不支援 python 3.6 版** 這樣的錯誤。 請改用 Python 3.5 或更早版本。 |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Python 的 .NET 實作具有 32 位元和 64 位元版本，除了提供 C#/F#/Visual Basic 互通性之外，還可存取 .NET API、標準 Python 偵錯 (但不包括 C++ 混合模式偵錯) 及混合式 IronPython/C# 偵錯。 不過，IronPython 並不支援虛擬環境。 |
| [Anaconda](https://www.continuum.io) | 由 Python 提供技術支援的開放式資料科學平台，它包含最新版的 CPython 和大多數難以安裝的套件。 如果您無法決定要使用哪一個解譯器，建議您使用此解譯器。 |
| [PyPy](https://www.pypy.org/) | Python 的高效能追蹤 JIT 實作，適合用來處理長時間執行的程式，以及您找出效能問題但找不到其他解決方案的情況。 可以與 Visual Studio 搭配運作，但對進階偵錯功能的支援有限。 |
| [Jython](https://www.jython.org/) | 「Java 虛擬機器」(JVM) 上的 Python 實作。 與 IronPython 類似，在 Jython 中執行的程式碼可以與 Java 類別和程式庫進行互動，但可能無法使用許多適用於 CPython 的程式庫。 可以與 Visual Studio 搭配運作，但對進階偵錯功能的支援有限。 |

開發人員如果想要為 Python 環境提供新形式的偵測，可以參閱 [PTVS 環境偵測 (英文)](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (github.com)。

## <a name="move-an-interpreter"></a>移動解譯器

如果您使用檔案系統將現有的解譯器移至新的位置，則 Visual Studio 不會自動偵測變更。

- 如果您原本透過 [Python 環境] 視窗指定解譯器的位置，請使用該視窗中的 [設定] 索引標籤來編輯其環境，以便識別新的位置。 請參閱[手動識別現有的環境](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)。

- 如果您已使用安裝程式安裝解譯器，則請使用下列步驟在新的位置中重新安裝解譯器：

  1. 將 Python 解譯器還原到其原始位置。
  2. 使用其安裝程式將它解除安裝，並一併清除登錄項目。
  3. 在所需的位置重新安裝解譯器。
  4. 重新啟動 Visual Studio，如此應該會自動偵測新的位置來取代舊的位置。

遵循此程序可確保識別解譯器位置 (由 Visual Studio 所使用) 的登錄項目已適當更新。 使用安裝程式也可以處理任何可能存在的其他副作用。

## <a name="see-also"></a>另請參閱

- [管理 Python 環境](managing-python-environments-in-visual-studio.md)
- [選取專案的解譯器](selecting-a-python-environment-for-a-project.md)
- [為相依性使用 requirements.txt](managing-required-packages-with-requirements-txt.md)
- [搜尋路徑](search-paths.md)
- [Python 環境視窗參考](python-environments-window-tab-reference.md)
