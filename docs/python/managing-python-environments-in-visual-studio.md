---
title: 管理 Python 環境與解譯器
description: 使用 [Python 環境] 視窗管理全域、虛擬和 conda 環境、安裝 Python 解譯器和套件，以及將環境指派給 Visual Studio 專案。
ms.date: 08/06/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- python
- data-science
ms.openlocfilehash: 26bcf0fa4d56d4e8df100a0d3e65904d065d8757
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254871"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>如何在 Visual Studio 中建立及管理 Python 環境

**Python 環境** 是您執行 python 程式碼的內容，其中包含全域、虛擬和 conda 環境。 環境是由解譯器、程式庫 (通常是 Python 標準程式庫) 及一組已安裝的套件所組成。 這些元件共同決定有效的語言建構和語法、您可存取的作業系統功能，以及您可以使用的套件。

在 Windows 上的 Visual Studio 中，您可以在本文所描述的 [Python 環境] 視窗中，管理環境並選取其中之一作為新專案的預設環境。 下列文章中可找到環境的其他方面：

- 針對任何指定的專案，您可以[選取特定環境](selecting-a-python-environment-for-a-project.md)，而不使用預設環境。

- 如需針對 Python 專案建立和使用虛擬環境的詳細資料，請參閱[使用虛擬環境](selecting-a-python-environment-for-a-project.md#use-virtual-environments)。

- 如果您想要在環境中安裝套件，請參閱[套件索引標籤參考](python-environments-window-tab-reference.md#packages-tab)。

- 若要安裝其他 Python 解譯器，請參閱[安裝 Python 解譯器](installing-python-interpreters.md)。 一般情況下，如果您下載及執行主線 Python 散發套件的安裝程式，Visual Studio 會偵測到有新的安裝和環境出現在 [Python 環境] 視窗中，因此可以選取專案。

如果您剛接觸 Visual Studio 中的 Python，下列文章也提供一般背景：

- [在 Visual Studio 中使用 Python](overview-of-python-tools-for-visual-studio.md)
- [在 Visual Studio 中安裝 Python 支援](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> 您無法管理 Python 程式碼的環境，此程式碼只會 **使用 [**  >  **開啟**  >  **資料夾**] 命令以資料夾的形式開啟。 您可以改為[從現有的程式碼建立 Python 專案](quickstart-01-python-in-visual-studio-project-from-existing-code.md)，即可享受 Visual Studio 的環境功能。
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> 您可以 **使用 [檔案**  >  **開啟**  >  **資料夾**] 命令來管理以資料夾形式開啟之 Python 程式碼的環境。 Python 工具列可讓您在所有偵測到的環境間進行切換，以及新增新的環境。 環境資訊會儲存在工作區 .vs 資料夾的 PythonSettings.json 檔案中。
::: moniker-end

## <a name="the-python-environments-window"></a>[Python 環境] 視窗

Visual Studio 知道的環境會顯示在 [Python 環境] 視窗中。 若要開啟視窗，可以使用下列方法之一：

- 選取 [**查看**  >  **其他 Windows**  >  **Python 環境**] 功能表命令。
- 在 **方案總管** 中，以滑鼠右鍵按一下專案的 [ **Python 環境**] 節點，然後選取 [ **View All Python 環境**：

    ::: moniker range="vs-2017"
    ![[方案總管] 中的「檢視所有環境」命令](media/environments/environments-view-all.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![[方案總管] 中的「檢視所有環境」命令](media/environments/environments-view-all-2019.png)
    ::: moniker-end

不論是上述哪一種情況，[Python 環境] 視窗都會顯示在 [方案總管] 旁：

::: moniker range="vs-2017"
![[Python Environments (Python 環境)] 視窗](media/environments/environments-default-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![[Python Environments (Python 環境)] 視窗](media/environments/environments-default-view-2019.png)
::: moniker-end

Visual Studio 會使用登錄尋找已安裝的全域環境 (在 [PEP 514](https://www.python.org/dev/peps/pep-0514/) 之後)，以及虛擬環境和 Conda 環境 (請參閱[環境的類型](#types-of-environments))。 如果在清單中沒有看到您預期的環境，請參閱[手動識別現有的環境](#manually-identify-an-existing-environment)。

當您選取清單中的環境時，Visual Studio 會在 [ **總覽** ] 索引標籤上顯示該環境的各種屬性和命令。例如，您可以在上圖中看到解譯器的位置是 *C:\Python36-32*。 [概觀] 索引標籤底部的四個命令各自都會開啟命令提示字元，其中已執行解譯器。 如需詳細資訊，請參閱 [Python 環境視窗索引標籤參考 - 概觀](python-environments-window-tab-reference.md#overview-tab)。

使用環境清單下的下拉式清單，切換到不同的索引標籤，例如 [套件] 和 [IntelliSense]。 [Python 環境視窗索引標籤參考](python-environments-window-tab-reference.md)也提供這些索引標籤的說明。

選取環境不會變更它與任何專案的關聯性。 在清單中以粗體顯示的預設環境，是 Visual Studio 用於任何新專案的環境。 若要使用不同環境來搭配新專案，請使用 [將此設定為新專案的預設環境] 命令。 在專案的內容中，您一律可以選取特定的環境。 如需詳細資訊，請參閱[選取專案的環境](selecting-a-python-environment-for-a-project.md)。

每個列出環境的右邊都有一個控制項，可開啟該環境的 **互動式** 視窗。 (在 Visual Studio 2017 15.5 版和更早版本中會出現另一個控制項，重新整理該環境的 IntelliSense 資料庫。 如需資料庫的詳細資料，請參閱 [環境視窗](python-environments-window-tab-reference.md) 索引標籤參考。 ) 

::: moniker range="vs-2017"
> [!Tip]
> 如果您將 [Python 環境] 視窗展開至足夠寬度，您便可以較完整地檢視環境，您可能會發現更方便使用。
>
> ![[Python Environments (Python 環境)] 視窗展開檢視](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Tip]
> 如果您將 [Python 環境] 視窗展開至足夠寬度，您便可以較完整地檢視環境，您可能會發現更方便使用。
>
> ![[Python Environments (Python 環境)] 視窗展開檢視](media/environments/environments-expanded-view-2019.png)
::: moniker-end

> [!Note]
> 雖然 Visual Studio 會遵守「系統-站台-套件」選項，但未提供從 Visual Studio 內變更它的方式。

### <a name="what-if-no-environments-appear"></a>如果沒有環境出現怎麼辦？

如果沒有環境出現，表示 Visual Studio 無法在標準安裝位置中偵測到任何 Python 安裝。 例如，您可能已安裝 Visual Studio 2017 或更新版本，但清除了 Python 工作負載安裝程式中的所有解譯器選項。 同樣地，您可能已安裝 Visual Studio 2015 或更早版本，但未手動安裝解譯器 (請參閱[安裝 Python 解譯器](installing-python-interpreters.md))。

如果您知道電腦上有 Python 解譯器，但 Visual Studio (任何版本) 未偵測到它，則請使用 **+ 自訂** 命令手動指定其位置。 請參閱下一節：[手動識別現有的環境](#manually-identify-an-existing-environment)。

> [!Tip]
> Visual Studio 會偵測現有解譯器的更新，例如使用 python.org 中的安裝程式將 Python 2.7.11 升級至2.7.14。在安裝過程中，較舊的環境會從 **Python 環境** 清單中消失，然後更新才會出現在其位置中。
>
> 不過，如果您使用檔案系統以手動方式移動解譯器和其環境時，Visual Studio 不會知道新的位置。 如需詳細資訊，請參閱[移動解譯器](installing-python-interpreters.md#move-an-interpreter)。

### <a name="types-of-environments"></a>環境的類型

Visual Studio 可以使用全域、虛擬和 Conda 環境。

#### <a name="global-environments"></a>全域環境

每個 Python 安裝 (例如，Python 2.7、Python 3.6、Python 3.7、Anaconda 4.4.0 等，請參閱 [安裝 Python 解釋](installing-python-interpreters.md) 器) 維護自己的 *全域環境*。 每個環境是由特定的 Python 解譯器、其標準程式庫、一組預先安裝的套件，以及您在該環境啟用時安裝的任何其他套件所組成。 將套件安裝到全域環境中，可將套件提供給使用該環境的所有專案使用。 如果環境位在檔案系統的受保護區域中 (例如 *c:\program files* 內)，則安裝套件需要系統管理員權限。

全域環境可提供給電腦上的所有專案使用。 在 Visual Studio 中，您選取一個全域環境做為預設環境。除非您特別針對某個專案選擇不同的環境，否則所有專案都會使用預設環境。 如需詳細資訊，請參閱[選取專案的環境](selecting-a-python-environment-for-a-project.md)。

#### <a name="virtual-environments"></a>虛擬環境

雖然在全域環境中工作很簡單便能夠開始，但該環境經過一段時間後，就會塞滿許多您為不同專案安裝的不同套件。 這類混亂的情形會讓您難以針對一組已知版本的特定套件來全面測試應用程式，而這正是您在組建伺服器或網頁伺服器上設定的環境類型。 當兩個專案需要的套件不相容，或是需要相同套件的不同版本時，也可能會發生衝突。

因此，開發人員通常會為專案建立「虛擬環境」。 虛擬環境是專案中子資料夾，其中包含特定解譯器的複本。 當您啟用虛擬環境時，您安裝的任何套件都只會安裝在該環境的子資料夾中。 如此當您在該環境中執行 Python 程式時，您會知道它只針對那些特定的套件執行。

Visual Studio 對於建立專案的虛擬環境提供直接的支援。 例如，如果您開啟專案，其中包含 *requirements.txt*，或從包含該檔案的範本建立專案，Visual Studio 會提示您自動建立虛擬環境並安裝這些相依性。

在開啟的專案內，您可以隨時建立新的虛擬環境。 在 [方案總管] 中，展開專案節點、以滑鼠右鍵按一下 [Python 環境]，然後選取 [新增虛擬環境]。 如需詳細資訊，請參閱[建立虛擬環境](./selecting-a-python-environment-for-a-project.md?view=vs-2019&preserve-view=true#create-a-virtual-environment-1)。

Visual Studio 提供的命令也可從虛擬環境產生 *requirements.txt* 檔案，方便您在其他電腦上重新建立環境。 如需詳細資訊，請參閱[使用虛擬環境](selecting-a-python-environment-for-a-project.md#use-virtual-environments)。

#### <a name="conda-environments"></a>Conda 環境

Conda 環境是使用 `conda` 工具建立的環境，或在 Visual Studio 2017 15.7 版及更新版本使用整合式 Conda 管理建立的環境。 (需要 Anaconda 或 Miniconda，可透過 Visual Studio 安裝程式取得，請參閱[安裝](installing-python-support-in-visual-studio.md#visual-studio-2019-and-visual-studio-2017)。)

::: moniker range="vs-2017"

1. 在 [Python 環境] 視窗中選取 [+ 建立 Conda 環境]，這會開啟 [建立新的 Conda 環境] 索引標籤：

    ![為新的 Conda 環境建立索引標籤](media/environments/environments-conda-1.png)

1. 在 [名稱] 欄位中輸入環境的名稱，在 [Python] 欄位中選取基底 Python 解譯器，然後選取 [建立]。

1. [輸出] 視窗會顯示新環境的進度，建立完成後會有一些 CLI 指示：

    ![成功建立 Conda 環境](media/environments/environments-conda-2.png)

1. 在 Visual Studio 中，您可以針對專案啟動 Conda 環境，如同您依[選取專案的環境](selecting-a-python-environment-for-a-project.md)中所述，對任何其他環境所做的一樣。

1. 若要在環境中安裝套件，請使用 [[套件] 索引標籤](python-environments-window-tab-reference.md#packages-tab)。
::: moniker-end

::: moniker range=">=vs-2019"

1. 在 [ **Python 環境**] 視窗中選取 [**新增環境 ...** ] (或從 python 工具列) 開啟 [**新增環境**] 對話方塊。 在該對話方塊中，選取 [Conda 環境] 索引標籤：

    ![[新增環境] 對話方塊中的 [Conda 環境] 索引標籤](media/environments/environments-conda-1-2019.png)

1. 設定下列欄位：

    | 欄位 | 描述 |
    | --- | --- |
    | Project | 要在其中建立環境的專案 (如果您在相同的 Visual Studio 解決方案中有多個專案)。 |
    | Name | Conda 環境的名稱。 |
    | 新增套件自 | 如果您有描述相依性的 *environment.yml* 檔案，請選擇 [環境檔案]，或選擇 **一或多個 Anaconda 套件名稱**，並在下方欄位中至少列出一個 Python 封裝或 Python 版本。 套件清單會指示 conda 建立 Python 環境。 若要安裝最新版的 Python，請使用 `python`；若要安裝特定版本，請使用 `python=,major>.<minor>` (就像在 `python=3.7` 中那樣)。 您也可以使用套件按鈕從一系列的功能表中選取 Python 版本和通用套件。 |
    | 設定為目前環境 | 建立環境之後，在所選取的專案中啟動新環境。 |
    | 將新專案設為預設環境 | 在 Visual Studio 中建立的任何新專案中，自動設定並啟動 conda 環境。 此選項和使用 [Python 環境] 視窗中的 [將此設定為新專案的預設環境] 是一樣的。 |
    | 在 Python 環境視窗中檢視 | 指定是否要在建立環境之後顯示 [Python 環境] 視窗。 |

    > [!Important]
    > 建立 conda 環境時，請務必使用 `environments.yml` 或套件清單至少指定一個 Python 版本或 Python 套件，這可以確保該環境包含 Python 執行階段。 如果沒有這樣做，Visual Studio 會忽略環境：[Python 環境] 視窗中不會顯示環境、不會設為專案目前的環境，且無法做為全域環境。
    >
    > 如果在沒有 Python 版本的情況下建立 conda 環境，請使用 `conda info` 命令查看 conda 環境資料夾的位置，然後手動將環境的子資料夾從該位置移除。

1. 選取 [建立] 並觀察 [輸出] 視窗中的進度。 建立作業完成之後，輸出中會包括幾個 CLI 指示：

    ![成功建立 Conda 環境](media/environments/environments-conda-2-2019.png)

1. 在 Visual Studio 中，您可以針對專案啟動 Conda 環境，如同您依[選取專案的環境](selecting-a-python-environment-for-a-project.md)中所述，對任何其他環境所做的一樣。

1. 若要在環境中安裝額外的套件，請使用[[套件] 索引標籤](python-environments-window-tab-reference.md#packages-tab)。
::: moniker-end

> [!Note]
> 如要取得 Conda 環境的最佳結果，請使用 Conda 4.4.8 或更新版本 (Conda 版本隨 Anaconda 版本而異)。 您可以透過 Visual Studio 安裝程式安裝適當版本的 Miniconda (Visual Studio 2019) 和 Anaconda (Visual Studio 2017)。

若要查看 Conda 環境儲存所在的 Conda 版本和其他資訊，請在 Anaconda 的命令提示字元中 (亦即 Anaconda 所在路徑的命令提示字元) 執行 `conda info`：

```cli
conda info
```

您的 Conda 環境資料夾隨即出現，如下所示：

```output
       envs directories : C:\Users\user\.conda\envs
                          c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
```

因為 Conda 環境未隨專案儲存，所以它們的表現類似全域環境。 例如，將新套件安裝到 Conda 環境，便會使得所有使用該環境的專案都能取得該套件。

若為 Visual Studio 2017 15.6 版或較舊版本，您可以如[手動識別現有的環境](#manually-identify-an-existing-environment)中所述手動指向它們來使用 Conda 環境。

Visual Studio 2017 15.7 版和更新版本會自動偵測 Conda 環境，並在 [Python 環境] 視窗中顯示它們，如下一節所述。

## <a name="manually-identify-an-existing-environment"></a>手動識別現有的環境

您可以使用下列步驟來識別安裝在非標準位置中的環境 (包括 Visual Studio 2017 15.6 版及較舊版本中的 Conda 環境)：

::: moniker range="vs-2017"

1. 在 [ **Python 環境**] 視窗中選取 [ **+ 自訂**]，開啟 [**設定**] 索引標籤：

    ![新自訂環境的預設檢視](media/environments/environments-custom-1.png)

1. 在 [Description (描述)] 欄位中，輸入環境的名稱。

1. 在 [**前置詞路徑**] 欄位中，輸入或流覽 (使用 **...**) 至解譯器的路徑。

1. 如果 Visual Studio 在該位置偵測到 Python 解譯器 (像如下所示的 Conda 環境路徑)，就會啟用 [自動偵測] 命令。 選取 [ **自動** 偵測] 會完成其餘的欄位。 您也可以手動完成這些欄位。

    ![啟用 [自動偵測] 命令](media/environments/environments-custom-2.png)

    ![使用 [自動偵測] 之後所完成的環境欄位](media/environments/environments-custom-3.png)

1. 欄位包含您要的值之後，請選取 [套用] 以儲存設定。 您現在可以使用該環境，如同 Visual Studio 內的其他環境。

1. 如果您需要移除手動識別的環境，請選取 [**設定**] 索引標籤上的 [**移除**] 命令。自動偵測到的環境不會提供此選項。 如需詳細資訊，請參閱[設定索引標籤](python-environments-window-tab-reference.md#configure-tab)。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 [ **Python 環境**] 視窗中選取 [**新增環境 ...** ] (或從 python 工具列) 開啟 [**新增環境**] 對話方塊。 在該對話方塊中，選取 [現有環境] 索引標籤：

    ![[新增環境] 對話方塊中的 [現有環境] 索引標籤](media/environments/environments-custom-1-2019.png)

1. 選取 [環境] 下拉式清單，然後選取 [自訂]：

    ![[新增環境] 對話方塊中的 [自訂環境] 選項](media/environments/environments-custom-2-2019.png)

1. 在對話方塊提供的欄位中，輸入或瀏覽 (使用 [...]) 至 [前置詞路徑] 下解譯器的路徑，這會填入大部分的其他欄位。 檢視那些值並視需要修改之後，請選取 [新增]。

    ![[新增環境] 對話方塊中用於指定自訂環境選項詳細資料的欄位](media/environments/environments-custom-3-2019.png)

1. 您隨時可以在 [Python 環境] 視窗中檢閱及修改環境詳細資料。 在該視窗中，選取環境，然後選取 [ **設定** ] 索引標籤。進行變更之後，請選取 **[套用** ] 命令。 您也可以使用 [移除] 命令移除環境 (不適用於自動偵測環境)。 如需詳細資訊，請參閱[設定索引標籤](python-environments-window-tab-reference.md#configure-tab)。
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>修正或刪除無效的環境

如果 Visual Studio 找到環境的登錄專案，但解譯器的路徑無效，[ **Python 環境** ] 視窗就會顯示具有刪除線字型的名稱：

::: moniker range="vs-2017"
![顯示無效環境的 [Python 環境] 視窗](media/environments/environments-invalid-entry.png)
::: moniker-end
::: moniker range=">=vs-2019"
![顯示無效環境的 [Python 環境] 視窗](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

若要修正您想保留的環境，請先嘗試使用其安裝程式的 **修復** 流程。 例如，標準 Python 3.x 的安裝程式即包含該選項。

若要修正沒有修復選項的環境，或要移除無效的環境，請直接使用下列步驟修改登錄。 當您對登錄進行變更時，Visual Studio 會自動更新 [ **Python 環境** ] 視窗。

1. 執行 *regedit.exe*。
1. 流覽至 **HKEY_LOCAL_MACHINE\SOFTWARE\Python** 或 **HKEY_CURRENT_USER\SOFTWARE\Python**。 若是 IronPython，請改為尋找 **IronPython**。
1. 展開符合發佈的節點，例如 CPython 為 **PythonCore**，Anaconda 為 **ContinuumAnalytics**。 若是 IronPython，請展開版本號碼節點。
1. 檢查 **InstallPath** 節點下的值：

    ![一般 CPython 安裝的登錄項目](media/environments/environments-registry-entries.png)

    - 若環境仍存在於您的電腦上，請將 **ExecutablePath** 的值變更為正確位置。 如有必要，也請修正 **(預設)** 和 **WindowedExecutablePath** 值。
    - 若環境不再存在於您的電腦上，而您想要從 [Python 環境] 視窗中予以移除，請刪除 **InstallPath** 的父節點，例如上圖中的 **3.6**。
    - **HKEY_CURRENT_USER\SOFTWARE\Python** 中的無效設定覆寫 **HKEY_LOCAL_MACHINE\SOFTWARE\Python** 中的設定

## <a name="see-also"></a>另請參閱

- [安裝 Python 解譯器](installing-python-interpreters.md)
- [選取專案的解譯器](selecting-a-python-environment-for-a-project.md)
- [為相依性使用 requirements.txt](managing-required-packages-with-requirements-txt.md)
- [搜尋路徑](search-paths.md)
- [Python 環境視窗參考](python-environments-window-tab-reference.md)