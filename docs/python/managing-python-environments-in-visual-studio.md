---
title: "如何在 Visual Studio 中管理 Python 環境與解譯器 | Microsoft Docs"
description: "如何在 Visual Studio 中使用 [Python 環境] 視窗，來為 Visual Studio 專案管理全域及虛擬環境、設定自訂環境、安裝 Python 解譯器、安裝套件、設定搜尋路徑，以及管理環境。"
ms.custom: 
ms.date: 03/05/2018
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
ms.openlocfilehash: 558ce58461b27bc9a86906278602d00d96377c63
ms.sourcegitcommit: 3285243d6c0521266053340fe06505885d12178b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2018
---
# <a name="managing-python-environments-in-visual-studio"></a>在 Visual Studio 中管理 Python 環境

Python「環境」是您執行 Python 程式碼的內容，其中包含全域、虛擬和 Conda 環境。 環境是由解譯器、程式庫 (通常是 Python 標準程式庫) 及一組已安裝的套件所組成。 這些元件共同決定有效的語言建構和語法、您可存取的作業系統功能，以及您可以使用的套件。

在 Windows 上的 Visual Studio 中，您可以在本文所描述的 [Python 環境](#managing-python-environments-in-visual-studio)視窗中，管理這些環境並選取其中之一作為新專案的預設環境。 對於任何給定的專案，您也可以選取特定的環境，而不使用預設的環境。

**注意**：如果您剛接觸 Visual Studio 中的 Python，請參閱下列文章以了解必要的背景：

- [在 Visual Studio 中使用 Python](overview-of-python-tools-for-visual-studio.md)
- [在 Visual Studio 中安裝 Python 支援](installing-python-support-in-visual-studio.md)

另請注意，針對僅開啟為資料夾 (使用 [檔案] > [開啟] > [資料夾] 命令) 的 Python 程式碼，您無法管理其環境。 您可以改為[從現有的程式碼建立 Python 專案](quickstart-01-python-in-visual-studio-project-from-existing-code.md)，即可享受 Visual Studio 的環境功能。

## <a name="types-of-environments"></a>環境的類型

### <a name="global-environments"></a>全域環境

每個 Python 安裝 (例如，Python 2.7、Python 3.6、Anaconda 4.4.0 等，請參閱[選取並安裝 Python 解譯器](installing-python-interpreters.md)) 都維持自己的全域環境。 每個環境是由特定的 Python 解譯器、其標準程式庫和一組預先安裝的套件所組成。 將套件安裝到全域環境中，可將套件提供給使用該環境的所有專案使用。 如果環境位在檔案系統的受保護區域中 (例如 `c:\program files` 內)，則安裝套件需要系統管理員權限。

全域環境可提供給電腦上的所有專案使用。 在 Visual Studio 中，您選取一個全域環境做為預設環境。除非您特別針對某個專案選擇不同的環境，否則所有專案都會使用預設環境。 如需詳細資訊，請參閱[選取專案的環境](selecting-a-python-environment-for-a-project.md)。

### <a name="virtual-environments"></a>虛擬環境

由於安裝到全域環境中的套件可供使用該環境的所有專案使用，因此當兩個專案所需的套件不相容，或所需的是相同套件的不同版本時，就可能發生衝突。 虛擬環境會使用全域環境的解譯器和標準程式庫，但是在隔離的資料夾中自行保有套件存放區，藉此避免類似的衝突。

在 Visual Studio 中，您可以針對特定專案建立一個虛擬環境，它會儲存在專案的子資料夾中 (請參閱[建立虛擬環境](selecting-a-python-environment-for-a-project.md#creating-a-virtual-environment))。 專案檔也會識別虛擬環境。 Visual Studio 也會在專案的 `requirements.txt` 檔案中，記錄您安裝到虛擬環境中的任何套件。 之後如果您共用專案，且其他開發人員在其電腦上開啟該專案，則 Visual Studio 會提供重新建立虛擬環境的選項。

### <a name="conda-environments"></a>Conda 環境

Conda 環境是使用 `conda` 工具建立的。 Conda 環境通常儲存在 Anaconda 安裝內的 `envs` 資料夾中，因此作用就類似於全域環境。 例如，將新套件安裝到 Conda 環境，便會使得所有使用該環境的專案都能取得該套件。

Visual Studio 目前還不會自動偵測 Conda 環境，但您可以手動將 Visual Studio 指向它。 請參閱[手動識別現有的環境](#manually-identifying-an-existing-environment)。

## <a name="the-python-environments-window"></a>[Python 環境] 視窗

Visual Studio 知道的環境會顯示在 [Python 環境] 視窗中。 若要開啟視窗，可以使用下列方法之一：

- 選取 [View (檢視)] > [Other Windows (其他視窗)] > [Python Environments (Python 環境)] 功能表命令。
- 在 [方案總管] 中專案的 [Python 環境] 節點上按一下滑鼠右鍵，然後選取 [檢視所有 Python 環境]：

    ![[方案總管] 中的「檢視所有環境」命令](media/environments-view-all.png)

不論是上述哪一種情況，[Python 環境] 視窗都會顯示為與 [方案總管] 同層級的索引標籤：

![[Python Environments (Python 環境)] 視窗](media/environments-default-view.png)

上列影像顯示 Visual Studio 偵測到兩個版本的 Python 3.6 (32-bit) 安裝，以及 Anaconda 5.0.0。

以粗體顯示的預設環境是 Python 3.6 (在此例中為 Anaconda 安裝的一部分)，Visual Studio 會將它用於所有的新專案。 視窗底部的命令適用於所選取的 Python 3.6 解譯器，如您所見，它們是 `C:\Python36-32` 中的特定安裝。 如果沒有看到您預期的環境，請參閱[手動識別現有的環境](#manually-identifying-an-existing-environment)。

在每個列出環境的右側，是可開啟該環境互動式視窗的控制項。 另一個會針對環境重新整理 IntelliSense 資料庫的控制項也可能會顯示 (請參閱[環境視窗參考](python-environments-window-tab-reference.md#intellisense-tab)以取得資料庫的相關詳細資料)。

環境清單下方是 [概觀]、[套件] 和 [IntelliSense] 選項的下拉式選取器，如 [Python 環境視窗參考](python-environments-window-tab-reference.md)中所述。 此外，如果您將 [Python 環境] 視窗展開至足夠寬度，便會以索引標籤的形式來顯示這些選項，以方便您使用：

![[Python Environments (Python 環境)] 視窗展開檢視](media/environments-expanded-view.png)

> [!Note]
> 雖然 Visual Studio 會遵守「系統-站台-套件」選項，但未提供從 Visual Studio 內變更它的方式。

|   |   |
|---|---|
| ![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片") | [觀看 Visual Studio 中之 Python 環境的影片 (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) (2 分 35 秒)。|

### <a name="what-if-no-environments-appear"></a>如果沒有環境出現怎麼辦？

如果沒有環境出現，表示 Visual Studio 無法在標準安裝位置中偵測到任何 Python 安裝。 例如，您可能已安裝 Visual Studio 2017，但清除了 Python 工作負載安裝程式中的所有解譯器選項。 同樣地，您可能已安裝 Visual Studio 2015 或更早版本，但未手動安裝解譯器 (請參閱[選取並安裝 Python 解譯器](installing-python-interpreters.md))。

如果您知道電腦上已安裝 Python 解譯器，但 Visual Studio (任何版本) 沒有偵測到它，請使用 [+ 自訂] 命令來手動指定它的位置。 請參閱下一節[手動識別現有的環境](#manually-identifying-an-existing-environment)。

> [!Tip]
> Visual Studio 會偵測對現有解譯器的更新，例如使用 python.org 的安裝程式將 Python 2.7.11 升級至 2.7.14。在安裝過程中，較舊的環境會先從 [Python 環境] 清單消失，然後更新環境才會顯示於該位置。
>
> 不過，如果您使用檔案系統以手動方式移動解譯器和其環境時，Visual Studio 不會知道新的位置。 如需詳細資訊，請參閱[移動解譯器](installing-python-interpreters.md#moving-an-interpreter)。

## <a name="manually-identifying-an-existing-environment"></a>手動識別現有的環境

您可以使用下列步驟來識別安裝在非標準位置中的環境 (包括 conda 環境)：

1. 在 [Python 環境] 視窗中，選取 [+ 自訂] 以開啟 [設定] 索引標籤：

    ![新自訂環境的預設檢視](media/environments-custom-1.png)

1. 在 [Description (描述)] 欄位中，輸入環境的名稱。

1. 在 [前置詞路徑] 欄位中輸入或瀏覽 (使用 [**...***]) 到解譯器的路徑。

1. 如果 Visual Studio 在該位置偵測到 Python 解譯器 (像如下所示的 Conda 環境路徑)，就會啟用 [自動偵測] 命令。 選取 [自動偵測] 以完成剩下的欄位。 您也可以手動完成這些欄位。

    ![啟用 [自動偵測] 命令](media/environments-custom-2.png)

    ![使用 [自動偵測] 之後所完成的環境欄位](media/environments-custom-3.png)

1. 欄位包含您要的值之後，請選取 [套用] 以儲存設定。 您現在可以使用該環境，如同 Visual Studio 內的其他環境。

1. 如果您需要移除手動識別的環境，請選取 [設定] 索引標籤上的 [移除] 命令。自動偵測環境不會提供這個選項。 如需詳細資訊，請參閱[設定索引標籤](python-environments-window-tab-reference.md#configure-tab)。

## <a name="see-also"></a>另請參閱

- [安裝 Python 解譯器](installing-python-interpreters.md)
- [選取專案的解譯器](selecting-a-python-environment-for-a-project.md)
- [將 requirements.txt 用於相依性](managing-required-packages-with-requirements-txt.md)
- [搜尋路徑](search-paths.md)
- [Python 環境視窗參考](python-environments-window-tab-reference.md)