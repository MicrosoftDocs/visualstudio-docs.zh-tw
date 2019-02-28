---
title: 選取要用於專案的 Python 解譯器和環境
description: 您可以特別選取要套用至特定專案的 Python 環境，包括 Anaconda 和虛擬環境。
ms.date: 02/11/2019
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b505a350cdb66cafb975585cb7ed0209104dabac
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56721800"
---
# <a name="how-to-select-a-python-environment-for-a-project"></a>如何選取要用於專案的 Python 環境

Python 專案中所有程式碼都會在特定環境的內容中執行，例如全域 Python 環境、Anaconda 環境、虛擬環境或 Conda 環境。 Visual Studio 也會使用該環境來進行偵錯、匯入和成員完成、語法檢查，以及任何其他需要 Python 版本特定語言服務和一組已安裝套件的工作。

Visual Studio 中所有新的 Python 專案一開始都會設定為使用預設全域環境，該環境會出現在 [方案總管] 中的 [Python 環境] 節點中：

![顯示在 [方案總管] 中的全域預設 Python 環境](media/environments-project.png)

若要變更專案的環境，請以滑鼠右鍵按一下 [Python 環境] 節點，然後選取 [新增/移除 Python 環境]。 在含有全域、虛擬和 Conda 環境的顯示清單中，選取您想要出現在 [Python 環境] 節點底下的所有項目：

![[Add/Remove Python Environments (新增/移除 Python 環境)] 對話方塊](media/environments-add-remove.png)

一旦您選取 [確定] 之後，所有已選取的環境都會顯示在 [Python 環境] 節點下。 目前啟用的環境會以粗體顯示：

![顯示在 [方案總管] 中的多個 Python 環境](media/environments-project-multiple.png)

若要快速啟用不同的環境，請在該環境名稱上按一下滑鼠右鍵，然後選取 [啟用環境]。 您的選擇會與專案一起儲存，日後每當您開啟專案時，都會啟用該環境。 如果您清除 [新增/移除 Python 環境] 對話方塊中的所有選項，則 Visual Studio 會啟用全域預設環境。

[Python 環境] 節點上的操作功能表也會提供其他命令：

| 命令 | 說明 |
| --- | --- |
| **新增虛擬環境** | 開始在專案中新建虛擬環境的程序。 請參閱[建立虛擬環境](#create-a-virtual-environment)。 |
| **新增現有的虛擬環境** | 提示您選取包含虛擬環境的資料夾，並將它新增至 [Python 環境] 底下的清單，但不會加以啟用。 [啟用現有的虛擬環境](#activate-an-existing-virtual-environment)。 |
| **建立 Conda 環境** | 切換至 [Python 環境] 視窗，您可在其中輸入環境名稱並指定其基底解譯器。 請參閱 [Conda 環境](managing-python-environments-in-visual-studio.md#conda-environments)。 |

## <a name="use-virtual-environments"></a>使用虛擬環境

虛擬環境是特定的 Python 解譯器與特定的一組程式庫的唯一組合，有別於其他的全域和 Conda 環境。 每個專案都有專屬的虛擬環境，並在專案資料夾中進行維護。 該資料夾包含環境的已安裝程式庫以及 *pyvenv.cfg* 檔案，其指定位於檔案系統上其他位置的環境「基底解譯器」路徑。 (也就是說，虛擬環境不包含解譯器複本，只包含它的連結)。

使用虛擬環境的其中一個優點是，即使經過一段時間的專案開發，虛擬環境仍會反映專案的確切相依性。 (反之，共用全域環境則會包含任意數目的程式庫，不論您是否在專案中使用這些程式庫)。如此一來，您即可輕鬆從虛擬環境建立 *requirements.txt* 檔案，然後用來在其他的開發或生產電腦上重新安裝這些相依性。 如需詳細資訊，請參閱[使用 requirements.txt 管理必要套件](managing-required-packages-with-requirements-txt.md)。

當您在 Visual Studio 中開啟的專案包含 *requirements.txt* 檔案時，Visual Studio 會自動提供可讓您重新建立虛擬環境的選項。 在未安裝 Visual Studio 的電腦上，您可以使用 `pip install -r requirements.txt` 還原套件。

由於虛擬環境包含基底解譯器的硬式編碼路徑，而且您可以使用 *requirements.txt* 重新建立環境，所以一般來說，您可以省略來自原始檔控制的整個虛擬環境資料夾。

下列各節說明如何啟用專案中的現有虛擬環境，以及如何建立新的虛擬環境。

在 Visual Studio 中，專案的虛擬環境啟用方式與任何其他項目一樣，都是透 過[方案總管] 的 [Python 環境] 節點來進行。

一旦虛擬環境新增至專案，即會出現在 [Python 環境] 視窗中。 接著，您可以像任何其他環境一樣將其啟用，並管理其套件。

### <a name="create-a-virtual-environment"></a>建立虛擬環境

您可以依照下列方式直接從 Visual Studio 建立新的虛擬環境：

1. 在 [方案總管] 中的 [Python 環境] 上按一下滑鼠右鍵，然後選取 [新增虛擬環境]，這會顯示下列對話方塊：

    ![建立虛擬環境](media/environments-add-virtual-1.png)

1. 在 [虛擬環境的位置] 欄位中，指定虛擬環境的路徑。 如果您只指定名稱，則會在目前專案中的子資料夾內以該名稱建立虛擬環境。

1. 選取一個環境作為基底解譯器，然後選取 [建立]。 Visual Studio 在設定環境並下載任何必要套件時，會顯示進度列。 此時，虛擬環境會出現在所包含專案的 [Python 環境] 視窗中。

1. 根據預設不會啟用虛擬環境。 若要為專案啟用虛擬環境，請以滑鼠右鍵按一下虛擬環境並選取 [啟用環境]。

> [!Note]
> 如果位置路徑識別的是現有虛擬環境，Visual Studio 會自動偵測基底解譯器 (使用環境的 *lib* 目錄中的 *orig-prefix.txt* 檔案) 並將 [建立] 按鈕變更為 [新增]。
>
> 新增虛擬環境時，如果 *requirements.txt* 檔案已經存在，則 [新增虛擬環境] 對話方塊就會顯示自動安裝套件的選項，讓您能夠輕鬆地在另一部電腦上重新建立環境：
>
> ![使用 requirements.txt 來建立虛擬環境](media/environments-requirements-txt.png)
>
> 無論使用哪個方法，結果都會和您使用 [新增現有虛擬環境] 命令的結果相同。

### <a name="activate-an-existing-virtual-environment"></a>啟用現有的虛擬環境

如果您已在其他位置建立虛擬環境，則可以依照下列方式為專案啟用虛擬環境：

1. 在 [方案總管] 中的 [Python 環境] 上按一下滑鼠右鍵，然後選取 [新增現有虛擬環境]。

1. 在顯示的 [瀏覽] 對話方塊中，瀏覽至包含虛擬環境的資料夾並加以選取，然後選取 [確定]。 如果 Visual Studio 在該環境中偵測到 *requirements.txt* 檔案，便會詢問是否要安裝那些套件。

1. 在幾分鐘之後，虛擬環境會出現在 [方案總管] 的 [Python 環境] 節點下方。 根據預設不會啟用虛擬環境，因此請以滑鼠右鍵按一下虛擬環境並選取 [啟用環境]。

### <a name="remove-a-virtual-environment"></a>移除虛擬環境

1. 在 [方案總管] 中，以滑鼠右鍵按一下虛擬環境然後選取 [移除]。

1. Visual Studio 會詢問是否要移除或刪除虛擬環境。 選取 [移除] 會使專案無法使用環境，但環境仍保留在檔案系統上。 選取 [刪除] 則會將環境從專案中移除，並從檔案系統中刪除它。 基底解譯器不會受到影響。

## <a name="view-installed-packages"></a>檢視安裝的套件

在 [方案總管] 中，展開任何特定環境的節點便可快速檢視在該環境中已安裝的套件 (表示當環境為作用中時，您可以在程式碼中匯入和使用那些套件)：

![[方案總管] 中環境的 Python 套件](media/environments-installed-packages.png)

若要安裝新的套件，在 [Python 環境] 視窗中 以滑鼠右鍵按一下環境，並選取 [安裝 Python 套件] 以切換至 [套件] 索引標籤。 輸入搜尋字詞 (通常是套件名稱)，Visual Studio 就會顯示相符的套件。

在 Visual Studio 中，套件 (及相依性) 是下載自 [Python 套件索引 (PyPI)](https://pypi.org) \(英文\)，您也可以在該處搜尋可用的套件。 Visual Studio 的狀態列和輸出視窗會顯示與該安裝相關的資訊。 若要將套件解除安裝，請在該套件上按一下滑鼠右鍵，然後選取 [移除]。

請注意，所顯示的項目可能未必正確，而安裝和解除安裝可能不可靠或不可用。 Visual Studio 會使用 pip 套件管理員 (如果可用)，並會在必要時下載並安裝它。 Visual Studio 也可以使用 easy_install 套件管理員。 使用 `pip` 或 `easy_install` 從命令列安裝的套件也會一併顯示。

另請注意，Visual Studio 目前不支援使用 `conda` 將套件安裝到 Conda 環境中。 請改為從命令列使用 `conda`。

> [!Tip]
> 有一個 pip 無法安裝套件的常見情況，就是當套件的 *\*.pyd* 檔案中包含原生元件的原始程式碼時。 如果未安裝所需的 Visual Studio 版本，pip 就無法編譯這些元件。 此情況中顯示的錯誤訊息為**錯誤：找不到 vcvarsall.bat**。 `easy_install` 通常能夠下載預先編譯的二進位檔，而您可以從 [https://aka.ms/VCPython27](https://aka.ms/VCPython27) 下載適用於舊版 Python 的編譯器。 如需詳細資訊，請參閱 Python 工具小組部落格中的[如何處理「找不到 vcvarsallbat」的困擾 (英文)](https://devblogs.microsoft.com/python/unable-to-find-vcvarsall-bat/)。

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中管理 Python 環境](managing-python-environments-in-visual-studio.md)
- [為相依性使用 requirements.txt](managing-required-packages-with-requirements-txt.md)
- [搜尋路徑](search-paths.md)
- [Python 環境視窗參考](python-environments-window-tab-reference.md)
