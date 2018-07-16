---
title: 管理 Python 環境與解譯器
description: 使用 [Python 環境] 視窗管理全域、虛擬和 conda 環境、安裝 Python 解譯器和套件，以及將環境指派給 Visual Studio 專案。
ms.date: 06/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 9ce601d169654c4fddca30b5e9853e18dcae9ac5
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "37342745"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>如何在 Visual Studio 中建立及管理 Python 環境

Python「環境」是您執行 Python 程式碼的內容，其中包含全域、虛擬和 Conda 環境。 環境是由解譯器、程式庫 (通常是 Python 標準程式庫) 及一組已安裝的套件所組成。 這些元件共同決定有效的語言建構和語法、您可存取的作業系統功能，以及您可以使用的套件。

在 Windows 上的 Visual Studio 中，您可以在本文所描述的 [Python 環境視窗](#the-python-environments-window)中，管理這些環境並選取其中之一作為新專案的預設環境。 對於任何指定的專案，您也可以[選取特定的環境](selecting-a-python-environment-for-a-project.md)，而不使用預設的環境。

**注意**：如果您剛接觸 Visual Studio 中的 Python，請參閱下列文章以了解必要的背景：

- [在 Visual Studio 中使用 Python](overview-of-python-tools-for-visual-studio.md)
- [在 Visual Studio 中安裝 Python 支援](installing-python-support-in-visual-studio.md)

另請注意，針對僅開啟為資料夾 (使用 [檔案] > [開啟] > [資料夾] 命令) 的 Python 程式碼，您無法管理其環境。 您可以改為[從現有的程式碼建立 Python 專案](quickstart-01-python-in-visual-studio-project-from-existing-code.md)，即可享受 Visual Studio 的環境功能。

如果您想要在環境中安裝套件，請參閱[套件索引標籤參考](python-environments-window-tab-reference.md#packages-tab)。

## <a name="types-of-environments"></a>環境的類型

### <a name="global-environments"></a>全域環境

每個 Python 安裝 (例如，Python 2.7、Python 3.6、Anaconda 4.4.0 等，請參閱[選取並安裝 Python 解譯器](installing-python-interpreters.md)) 都維持自己的全域環境。 每個環境是由特定的 Python 解譯器、其標準程式庫和一組預先安裝的套件所組成。 將套件安裝到全域環境中，可將套件提供給使用該環境的所有專案使用。 如果環境位在檔案系統的受保護區域中 (例如 `c:\program files` 內)，則安裝套件需要系統管理員權限。

全域環境可提供給電腦上的所有專案使用。 在 Visual Studio 中，您選取一個全域環境做為預設環境。除非您特別針對某個專案選擇不同的環境，否則所有專案都會使用預設環境。 如需詳細資訊，請參閱[選取專案的環境](selecting-a-python-environment-for-a-project.md)。

### <a name="virtual-environments"></a>虛擬環境

由於安裝到全域環境中的套件可供使用該環境的所有專案使用，因此當兩個專案所需的套件不相容，或所需的是相同套件的不同版本時，就可能發生衝突。 虛擬環境會使用全域環境的解譯器和標準程式庫，但是在隔離的資料夾中自行保有套件存放區，藉此避免類似的衝突。

在 Visual Studio 中，您可以針對特定專案建立一個虛擬環境，它會儲存在專案的子資料夾中。 Visual Studio 提供的命令可從虛擬環境生產 `requirements.txt` 檔案，方便您在其他電腦上重新建立環境。 如需詳細資訊，請參閱[使用虛擬環境](selecting-a-python-environment-for-a-project.md#using-virtual-environments)。

### <a name="conda-environments"></a>Conda 環境

Conda 環境是使用 `conda` 工具建立的環境，或在 Visual Studio 2017 15.7 版及更新版本使用整合式 Conda 管理建立的環境。 (需要 Anaconda 或 Miniconda，Anaconda 可透過 Visual Studio 安裝程式取得，請參閱[安裝 - Visual Studio 2017](installing-python-support-in-visual-studio.md#visual-studio-2017)。)

> [!Note]
> 如要取得 Conda 環境的最佳結果，請使用 Conda 4.4.8 或更新版本 (Conda 版本隨 Anaconda 版本而異)。 從 Visual Studio 2017 安裝程式安裝 Anaconda 5.1

若要查看 Conda 環境儲存所在的 Conda 版本和其他資訊，請在 Anaconda 的命令提示字元中 (亦即 Anaconda 所在路徑的命令提示字元) 執行 `conda info`：

```cli
conda info
```

您的 Conda 環境資料夾隨即出現，如下所示：

```output
       envs directories : c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
                          C:\Users\user\.conda\envs
```

因為 Conda 環境未隨專案儲存，所以它們的表現類似全域環境。 例如，將新套件安裝到 Conda 環境，便會使得所有使用該環境的專案都能取得該套件。

若為 Visual Studio 2017 15.6 版或較舊版本，您可以如[手動識別現有的環境](#manually-identify-an-existing-environment)中所述手動指向它們來使用 Conda 環境。

Visual Studio 2017 15.7 版和更新版本會自動偵測 Conda 環境，並在 [Python 環境] 視窗中顯示它們，如下一節所述。

## <a name="the-python-environments-window"></a>[Python 環境] 視窗

Visual Studio 知道的環境會顯示在 [Python 環境] 視窗中。 若要開啟視窗，可以使用下列方法之一：

- 選取 [檢視] > **[其他視窗]** > **[Python 環境]** 功能表命令。
- 在 [方案總管] 中專案的 [Python 環境] 節點上按一下滑鼠右鍵，然後選取 [檢視所有 Python 環境]：

    ![[方案總管] 中的「檢視所有環境」命令](media/environments-view-all.png)

不論是上述哪一種情況，[Python 環境] 視窗都會顯示為與 [方案總管] 同層級的索引標籤：

![[Python Environments (Python 環境)] 視窗](media/environments-default-view.png)

Visual Studio 遵循 [PEP 514](https://www.python.org/dev/peps/pep-0514/) 來識別使用登錄來安裝的環境。 如果在清單中沒有看到您預期的環境，請參閱[手動識別現有的環境](#manually-identify-an-existing-environment)。

在清單中選取環境，會在 [概觀] 索引標籤上顯示該環境的各種屬性與指令。例如，您在上圖中可見，解譯器的位置是 `C:\Python36-32`。 使用環境清單下的下拉式清單，切換到不同的索引標籤，例如 [套件] 和 [IntelliSense]。 這些索引標籤描述於 [Python 環境視窗索引標籤參考](python-environments-window-tab-reference.md)。

選取環境不會以任何方式啟動它。 在清單中以粗體顯示的預設環境，是目前已啟動的環境，Visual Studio 會用於任何新的專案。 若要啟用不同的環境，請使用 [將此設定為新專案的預設環境] 命令。 在專案的內容中，您一律可以啟用不同的環境。 如需詳細資訊，請參閱[選取專案的環境](selecting-a-python-environment-for-a-project.md)。

在每個列出環境的右側，是可開啟該環境互動式視窗的控制項。 (在 Visual Studio 2017 15.5 版和較舊版本中會出現另一個控制項，重新整理該環境的 IntelliSense 資料庫。 如需資料庫的詳細資料，請參閱[環境視窗索引標籤參考](python-environments-window-tab-reference.md#intellisense-tab)。)

> [!Tip]
> 如果您將 [Python 環境] 視窗展開至足夠寬度，您便可以較完整地檢視環境，您可能會發現更方便使用。
>
> ![[Python Environments (Python 環境)] 視窗展開檢視](media/environments-expanded-view.png)

> [!Note]
> 雖然 Visual Studio 會遵守「系統-站台-套件」選項，但未提供從 Visual Studio 內變更它的方式。

|   |   |
|---|---|
| ![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片") | [觀看 Visual Studio 中之 Python 環境的影片 (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) (2 分 35 秒)。|

### <a name="what-if-no-environments-appear"></a>如果沒有環境出現怎麼辦？

如果沒有環境出現，表示 Visual Studio 無法在標準安裝位置中偵測到任何 Python 安裝。 例如，您可能已安裝 Visual Studio 2017，但清除了 Python 工作負載安裝程式中的所有解譯器選項。 同樣地，您可能已安裝 Visual Studio 2015 或更早版本，但未手動安裝解譯器 (請參閱[安裝 Python 解譯器](installing-python-interpreters.md))。

如果您知道電腦上已安裝 Python 解譯器，但 Visual Studio (任何版本) 沒有偵測到它，請使用 [+ 自訂] 命令來手動指定它的位置。 請參閱下一節：[手動識別現有的環境](#manually-identify-an-existing-environment)。

> [!Tip]
> Visual Studio 會偵測對現有解譯器的更新，例如使用 python.org 的安裝程式將 Python 2.7.11 升級至 2.7.14。在安裝過程中，較舊的環境會先從 [Python 環境] 清單消失，然後更新環境才會顯示於該位置。
>
> 不過，如果您使用檔案系統以手動方式移動解譯器和其環境時，Visual Studio 不會知道新的位置。 如需詳細資訊，請參閱[移動解譯器](installing-python-interpreters.md#moving-an-interpreter)。

## <a name="fix-invalid-environments"></a>修正無效的環境

若 Visual Studio 找到環境的登錄項目，但解譯器的路徑無效，[Python 環境] 視窗就會以有刪除線的字型顯示名稱：

![顯示無效環境的 [Python 環境] 視窗](media/environments-invalid-entry.png)

若要修正您想保留的環境，請先嘗試使用其安裝程式的**修復**流程。 例如，標準 Python 3.x 的安裝程式即包含該選項。

若要修正沒有修復選項的環境，或要移除無效的環境，請直接使用下列步驟修改登錄。 Visual Studio 會在您對登錄進行變更時，自動更新 [Python 環境] 視窗。

1. 執行 `regedit.exe`。
1. 若是 32 位元解譯器，請瀏覽到 `HKEY_LOCAL_MACHINE\SOFTWARE\Python`；若是 64 位元解譯器，則請瀏覽到 `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python`。 若是 IronPython，請改為尋找 `IronPython`。
1. 展開符合發佈的節點，例如 CPython 為 `PythonCore`，Anaconda 為 `ContinuumAnalytics`。 若是 IronPython，請展開版本號碼節點。
1. 檢查 `InstallPath` 節點下的值：

    ![一般 CPython 安裝的登錄項目](media/environments-registry-entries.png)

    - 若環境仍存在於您的電腦上，請將 `ExecutablePath` 的值變更為正確位置。 如有必要，也請修正 `(Default)` 和 `WindowedExecutablePath` 值。
    - 若環境不再存在於您的電腦上，而您想要從 [Python 環境] 視窗中予以移除，請刪除 `InstallPath` 的父節點，如上圖中的 `3.6`。

<a name="manually-identifying-an-existing-environment"></a>

## <a name="manually-identify-an-existing-environment"></a>手動識別現有的環境

您可以使用下列步驟來識別安裝在非標準位置中的環境 (包括 Visual Studio 2017 15.6 版及較舊版本中的 Conda 環境)：

1. 在 [Python 環境] 視窗中，選取 [+ 自訂] 以開啟 [設定] 索引標籤：

    ![新自訂環境的預設檢視](media/environments-custom-1.png)

1. 在 [Description (描述)] 欄位中，輸入環境的名稱。

1. 在 [前置詞路徑] 欄位中輸入或瀏覽 (使用 [**...***]) 到解譯器的路徑。

1. 如果 Visual Studio 在該位置偵測到 Python 解譯器 (像如下所示的 Conda 環境路徑)，就會啟用 [自動偵測] 命令。 選取 [自動偵測] 以完成剩下的欄位。 您也可以手動完成這些欄位。

    ![啟用 [自動偵測] 命令](media/environments-custom-2.png)

    ![使用 [自動偵測] 之後所完成的環境欄位](media/environments-custom-3.png)

1. 欄位包含您要的值之後，請選取 [套用] 以儲存設定。 您現在可以使用該環境，如同 Visual Studio 內的其他環境。

1. 如果您需要移除手動識別的環境，請選取 [設定] 索引標籤上的 [移除] 命令。自動偵測環境不會提供這個選項。 如需詳細資訊，請參閱[設定索引標籤](python-environments-window-tab-reference.md#configure-tab)。

## <a name="create-a-conda-environment"></a>建立 Conda 環境

*Visual Studio 2017 15.7 版和更新版本。*

1. 在 [Python 環境] 視窗中選取 [+ 建立 Conda 環境]，這會開啟 [建立新的 Conda 環境] 索引標籤：

    ![為新的 Conda 環境建立索引標籤](media/environments-conda-1.png)

1. 在 [名稱] 欄位中輸入環境的名稱，在 [Python] 欄位中選取基底 Python 解譯器，然後選取 [建立]。

1. [輸出] 視窗會顯示新環境的進度，建立完成後會有一些 CLI 指示：

    ![成功建立 Conda 環境](media/environments-conda-2.png)

1. 在 Visual Studio 中，您可以針對專案啟動 Conda 環境，如同您依[選取專案的環境](selecting-a-python-environment-for-a-project.md)中所述，對任何其他環境所做的一樣。

1. 若要在環境中安裝套件，請使用 [[套件] 索引標籤](python-environments-window-tab-reference.md#packages-tab)。

## <a name="see-also"></a>另請參閱

- [安裝 Python 解譯器](installing-python-interpreters.md)
- [選取專案的解譯器](selecting-a-python-environment-for-a-project.md)
- [將 requirements.txt 用於相依性](managing-required-packages-with-requirements-txt.md)
- [搜尋路徑](search-paths.md)
- [Python 環境視窗參考](python-environments-window-tab-reference.md)