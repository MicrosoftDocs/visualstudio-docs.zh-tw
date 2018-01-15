---
title: "Visual Studio 中的 Python 環境 | Microsoft Docs"
ms.custom: 
ms.date: 07/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "11"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: 4f190d02850f1effc9e1597d14fecf323de68356
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2018
---
# <a name="python-environments"></a>Python 環境

Visual Studio 中的 Python 可讓您輕鬆管理多個 Python 環境，以及針對不同的專案輕鬆在這些環境之間進行切換。

**注意**︰如果您不熟悉 Visual Studio 中的 Python，請先參閱下列主題，因為本文的討論以這些主題為基礎︰

- [在 Visual Studio 中使用 Python](python-in-visual-studio.md)
- [在 Visual Studio 中安裝 Python 支援](installation.md)

一律執行 Python 程式碼的 Python「環境」，其由解譯器、程式庫 (通常是 Python 標準程式庫) 及一組已安裝的套件所組成。 這些元件一起決定哪些語言建構和語法有效、您可存取什麼作業系統功能，以及您可以使用哪些套件。

在 Visual Studio 中，環境也包含環境程式庫的 IntelliSense 資料庫，因此您只要在 Visual Studio 編輯器中鍵入 `import` 之類的陳述式，就會自動顯示可用的程式庫清單及這些程式庫內的模組。

開發人員通常只會使用單一全域 Python 環境。 不過，其他開發人員需要管理多個全域環境、專案特定環境和虛擬環境，如本主題所述：

- [選取並安裝 Python 解譯器](#selecting-and-installing-python-interpreters)
- [在 Visual Studio 中管理 Python 環境](#managing-python-environments-in-visual-studio)
- [全域環境](#global-environments)
- [專案特定環境](#project-specific-environments)
- [虛擬環境](#virtual-environments)
- [安裝必要套件](#managing-required-packages)
- [搜尋路徑](#search-paths)

如需影片介紹，請觀看 [Managing Python Environments](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) (管理 Python 環境，Microsoft Virtual Academy，2 分 35 秒)。

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Managing-Python-Environments-qrDmN4LWE_8305918567]

## <a name="selecting-and-installing-python-interpreters"></a>選取並安裝 Python 解譯器

除了 Visual Studio 2017 之外，Python 解譯器並未隨附 Python 支援，因此您必須安裝下列其中之一，才能執行您的程式碼。 一般而言，Visual Studio 會自動偵測新安裝的解譯器，並為每一個解譯器設定環境。 如果偵測不到安裝的環境，請參閱[為現有的解譯器建立環境](#creating-an-environment-for-an-existing-interpreter)。

| 解譯器 | 描述 |
| --- | --- |
| [CPython](https://www.python.org/) | 這是「原生」且最常用的解譯器，提供 32 位元和 64 位元版本 (建議使用 32 位元)。 包含最新的語言功能、最大的 Python 套件相容性、完整的偵錯支援，以及與 [IPython](http://ipython.org/) 的互通性。 另請參閱：[Should I use Python 2 or Python 3?](http://wiki.python.org/moin/Python2orPython3) (我應該使用 Python 2 還是 Python 3？) 請注意，Visual Studio 2015 及更早版本不支援 Python 3.6，因此可能會出現「不支援 python 3.6 版」的錯誤。 請改用 Python 3.5 或更早版本。 |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Python 的 .NET 實作具有 32 位元和 64 位元版本，除了提供 C#/F#/Visual Basic 互通性之外，還可存取 .NET API、標準 Python 偵錯 (但不包括 C++ 混合模式偵錯) 及混合式 IronPython/C# 偵錯。 不過，IronPython 並不支援虛擬環境。 |
| [Anaconda](https://www.continuum.io) | 由 Python 提供技術支援的開放式資料科學平台，它包含最新版的 CPython 和大多數難以安裝的套件。 如果您無法決定要使用哪一個解譯器，建議您使用此解譯器。 |
| [PyPy](http://www.pypy.org/) | Python 的高效能追蹤 JIT 實作，適合用來處理長時間執行的程式，以及您找出效能問題但找不到其他解決方案的情況。 可以與 Visual Studio 搭配運作，但對進階偵錯功能的支援有限。 |
| [Jython](http://www.jython.org/) | 「Java 虛擬機器」(JVM) 上的 Python 實作。 與 IronPython 類似，在 Jython 中執行的程式碼可以與 Java 類別和程式庫進行互動，但可能無法使用許多適用於 CPython 的程式庫。 可以與 Visual Studio 搭配運作，但對進階偵錯功能的支援有限。 |

開發人員如果想要為 Python 環境提供新形式的偵測，可以參閱 [PTVS 環境偵測 (英文)](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (github.com)。

## <a name="managing-python-environments-in-visual-studio"></a>在 Visual Studio 中管理 Python 環境

若要開啟 [Python Environments (Python 環境)] 視窗，請執行下列其中一項操作：

1. 選取 [View (檢視)] > [Other Windows (其他視窗)] > [Python Environments (Python 環境)] 功能表命令。
1. 在 [方案總管] 中某個專案的 [Python Environments (Python 環境)] 上按一下滑鼠右鍵，然後選取 [View All Python Environments (檢視所有 Python 環境)]：

    ![[方案總管] 中的「檢視所有環境」命令](media/environments-view-all.png)

不論是上述哪一種情況，[Python Environments (Python 環境)] 視窗都會顯示為與 [方案總管] 同層級的索引標籤：

![[Python Environments (Python 環境)] 視窗](media/environments-default-view.png)

上例顯示 Python 3.4 (32 位元 CPython) 已隨 32 位元和 64 位元版本的 IronPython 2.7 安裝。 在本例中，以粗體顯示的預設環境是 Python 3.4，用於所有新的專案。 如果未看到列出任何環境，即表示您已安裝 Visual Studio 2015 或更舊版本的 Python Tools for Visual Studio，但尚未安裝 Python 解譯器 (請參閱上述的[選取並安裝 Python 解譯器](#selecting-and-installing-python-interpreters))。

> [!Tip]
> 當 [Python 環境] 視窗變窄時 (如上所示)，環境會列在上方，而各種索引標籤會列在下方。 不過，將視窗展開到足夠的寬度，會變更為可能較方便您使用的寬型檢視。
>
> ![[Python Environments (Python 環境)] 視窗展開檢視](media/environments-expanded-view.png)

> [!Note]
> 雖然 Visual Studio 會遵守「系統-站台-套件」選項，但未提供從 Visual Studio 內變更它的方式。

### <a name="creating-an-environment-for-an-existing-interpreter"></a>為現有的解譯器建立環境

Visual Studio 通常會透過檢查登錄來找出安裝的 Python 解譯器 (依照 [PEP 514 - Windows 登錄中的 Python 註冊](https://www.python.org/dev/peps/pep-0514/)) \(英文)\。 不過，如果解譯器以非標準方式安裝，Visual Studio 可能無法找到解譯器。 在這種情況下，您可以依照下列方式，將 Visual Studio 直接指向解譯器：

1. 在 [[Python 環境] 視窗](#managing-python-environments-in-visual-studio)中選取 [+ 自訂...]，這會建立一個新環境並開啟 [[設定] 索引標籤](#configure-tab) (請見下方說明)。

    ![新自訂環境的預設檢視](media/environments-custom-1.png)

1. 在 [Description (描述)] 欄位中，輸入環境的名稱。
1. 在 [Prefix path (前置路徑)] 欄位中，輸入或瀏覽至解譯器的路徑。
1. 選取 [Auto Detect (自動偵測)] 來讓 Visual Studio 完成其餘欄位，或是手動完成它們。
1. 選取 [Apply (套用)] 來儲存環境。
1. 如果您需要移除環境，請在 [Configure (設定)] 索引標籤上選取 [Remove (移除)]。自動偵測環境不會提供這個選項。 如需詳細資訊，請參閱下一章節。

### <a name="moving-an-existing-interpreter"></a>移動現有的解譯器

如果您將現有的解譯器移至檔案系統上新的位置，Visual Studio 不會自動偵測變更。 您必須透過手動步驟來更新 [環境] 視窗中的清單：

- 如果您最初是針對該解譯器來建立環境，請編輯該環境以指向新的位置。

- 如果最初是自動偵測的環境，則環境是使用特定的安裝程式安裝在電腦上，而該安裝程式會建立登錄項目以供 Visual Studio 檢查。 在此情況下，請先將 Python 解譯器還原到其原始位置。 然後使用安裝程式將它解除安裝，以清除登錄項目。 接著，在所需的位置重新安裝解譯器。 重新啟動 Visual Studio，應該就會自動偵測新的位置。 此程序可確保正確地套用安裝程式的任何其他副作用。

### <a name="overview-tab"></a>Overview (概觀) 索引標籤

提供環境的基本資訊和命令：

![Python 環境的 [Oview (概觀)] 索引標籤](media/environments-overview-tab.png)

| 命令 | 描述 |
| --- | --- |
| 將此環境設為新專案的預設值 | 設定使用中環境，可能會導致在載入 IntelliSense 資料庫時，Visual Studio 短暫沒有反應。 環境如果含有許多套件，則無反應的時間可能會更長。 |
| 前往散發者的網站 | 將瀏覽器開啟至 Python 發行所提供的 URL。 例如，Python 3.x 會移至 python.org。 |
| 開啟互動式視窗 | 在 Visual Studio 內開啟此環境的[互動式 (REPL) 視窗](interactive-repl.md)，並套用任何[啟動指令碼 (請參閱下面)](#startup-scripts)。 |
| 使用 IPython 互動模式 | 設定時，預設會開啟 IPython 的互動式視窗。 此已啟用的內嵌繪圖和擴充的 IPython 語法，例如 `name?` 檢視說明，而 `!command` 適用於殼層命令。 使用需要額外套件的 Anaconda 發佈時，建議使用此選項。 如需詳細資訊，請參閱[在互動式視窗中使用 IPython](interactive-repl-ipython.md)。 |
| 在 PowerShell 中開啟 | 在 PowerShell 命令視窗中啟動解譯器。 |
| (資料夾連結) | 可讓您快速存取環境的安裝資料夾、python.exe 解譯器和 pythonw.exe 解譯器。 第一個會在 Windows 檔案總管中開啟，後面兩個則會開啟主控台視窗。 |

#### <a name="startup-scripts"></a>啟動指令碼

因為您在日常工作流程中使用互動式視窗，所以您可能會開發定期使用的協助程式函式。 例如，您可以建立可在 Excel 中開啟 DataFrame 的函式，然後將該程式碼儲存為啟動指令碼，讓它一律可在互動式視窗中使用。

啟動指令碼包含互動式視窗所載入並自動執行的程式碼，包括匯入、函式定義，以及文字形式的任何其他項目。 這類指令碼是使用兩種方式進行參考：

1. 當您安裝環境時，Visual Studio 會建立資料夾 `Documents\Visual Studio 2017\Python Scripts\<environment>`，其中 &lt;environment&gt' 符合環境的名稱。 您可以使用 [探索互動式指令碼] 命令，輕鬆地巡覽至環境特定資料夾。 當您啟動該環境的互動式視窗時，只要依字母順序在這裡找到 `.py` 檔案，就會載入並執行互動式視窗。

1. [工具] > [選項] > [Python 工具] > [互動式視窗] 索引標籤中的 [指令碼] 控制項 (請參閱[互動式視窗選項](options.md#interactive-windows-options)) 是用來指定所有環境中載入和執行之啟動指令碼的其他資料夾。 不過，此功能目前無法使用。

### <a name="configure-tab"></a>Configure (設定) 索引標籤

如果顯示，會包含如下表所述的詳細資料。 如果沒有此索引標籤，即表示目前由 Visual Studio 自動管理所有詳細資料。

![Python 環境的 [Configure (設定)] 索引標籤](media/environments-configure-tab.png)

| 欄位 | 描述 |
| --- | --- |
| **描述** | 要賦予環境的名稱。 |
| **Prefix path (前置路徑)** | 解譯器的基底資料夾位置。 填入此值並按一下 [自動偵測] 之後，Visual Studio 就會嘗試為您填入其他欄位。 |
| **Interpreter path (解譯器路徑)** | 解譯器可執行檔的路徑，通常是前置路徑後面再接著 `python.exe` |
| **Windowed interpreter (Windows 解譯器)** | 非主控台可執行檔的路徑，通常是前置路徑後面再接著 `pythonw.exe`。 |
| **Library path (程式庫路徑)** | 指定標準程式庫的根目錄，但如果 Visual Studio 能夠從解譯器要求更精確的路徑，則可以忽略這個值。 |
| **Language version (語言版本)** | 從下拉式功能表中選取。 |
| **架構** | 通常會自動偵測並填入，否則會指定 32 位元或 64 位元。 |
| **Path environment variable (路徑環境變數)** | 解譯器用來尋找搜尋路徑的環境變數。 Visual Studio 會在啟動 Python 時變更變數的值，使其包含專案的搜尋路徑。 通常這個屬性應該設定為 `PYTHONPATH`，但有些解譯器會使用不同的值。 |

### <a name="pip-tab"></a>pip 索引標籤

管理安裝在環境中的套件，讓您也能夠搜尋並安裝新的套件 (包括任何相依性)。 搜尋會篩選您目前已安裝的套件和 [PyPI](https://pypi.python.org)。 您也可以在搜尋方塊中直接輸入任何 `pip install` 命令，包括 `--user` 或 `--no-deps` 之類的旗標。

![Python 環境的 [pip] 索引標籤](media/environments-pip-tab.png)

安裝套件時會在環境於檔案系統的 `Lib` 資料夾內建立子資料夾。 例如，如果您已在 `c:\Python36` 中安裝 Python 3.6，則會將套件安裝在 `c:\Python36\Lib` 中；如果已在 `c:\Program Files\Anaconda3` 中安裝 Anaconda3，則會將套件安裝在 `c:\Program Files\Anaconda3\Lib` 中。

在後者的情況下，因為環境位於檔案系統的受保護區域 `c:\Program Files` 中，所以 Visual Studio 必須提高權限來執行 `pip install` 以允許它建立套件子資料夾。 需要提高權限時，Visual Studio 會顯示「可能需要系統管理員權限才可安裝、更新或移除此環境的套件」提示：

![套件安裝的提高權限提示](media/environments-pip-elevate.png)

[立即提高權限] 會將系統管理權限授與 pip 以進行單一作業、主題，也會授與權限的任何作業系統提示。 選取 [在沒有系統管理員權限的情況下繼續] 會嘗試安裝套件，但在嘗試建立包含「錯誤: 無法建立 'C:\Program Files\Anaconda3\Lib\site-packages\png.py': 權限遭拒」這類輸出的資料夾時，pip 會失敗。

選取 [安裝或移除套件時一律提高權限] 可防止在環境有問題時顯示對話方塊。 若要再次顯示對話方塊，請移至 [工具] > [選項] > [Python 工具] > [一般]，然後選取 [重設所有永久隱藏的對話方塊] 按鈕。

在這個相同的選項索引標籤中，您也可以選取 [一律以系統管理員身分執行 pip] 來隱藏所有環境的對話方塊。 請參閱[選項 - 一般索引標籤](options.md#general-options)。

### <a name="intellisense-tab"></a>IntelliSense 索引標籤

顯示 IntelliSense 完成資料庫的目前狀態：

![Python 環境的 [IntelliSense] 索引標籤](media/environments-intellisense-tab.png)

此資料庫包含環境所有程式庫的中繼資料，並可改善 IntelliSense 速度及降低記憶體使用量。 當 Visual Studio 偵測到新環境 (或您新增環境) 時，會透過分析程式庫原始程式檔來自動開始編譯資料庫。 視所安裝的項目而定，這個程序會花費一分鐘到一小時或數小時不等的時間。 (例如，Anaconda 隨附許多程式庫，因此就需要一些時間來編譯資料庫)。完成之後，您會獲得詳細的 IntelliSense，而在您安裝其他程式庫之前，就不需要再次重新整理資料庫 (使用 [Refresh DB] (重新整理資料庫) 按鈕)。

資料尚未經過編譯的程式庫會標示 **!**；如果環境的資料庫尚未完成，則 **!** 也會出現在主要環境清單中該資料庫的旁邊。

## <a name="global-environments"></a>全域環境

全域 (或全系統) 環境可供電腦上您的所有專案使用。 Visual Studio 通常會自動偵測全域環境，而這些環境可在 [[Python 環境] 視窗](#managing-python-environments-in-visual-studio)中檢視。 如果未偵測，您可以透過同一個視窗手動新增環境。

Visual Studio 會針對所有新專案使用預設環境，來執行、偵錯、檢查語法、顯示匯入和成員完成狀況，以及任何其他需要環境的工作。 變更預設環境會影響所有尚未新增[專案特定環境](#project-specific-environments) (接下來將會說明) 的專案。

## <a name="project-specific-environments"></a>專案特定環境

專案特定環境可確保讓專案忽略預設全域環境，而一律在特定的環境中執行。 例如，如果全域預設環境是 CPython，但專案需要的是 IronPython 及某些未安裝在全域環境中的程式庫，則專案特定環境就有其必要性。

專案環境會列在 [方案總管] 的 [Python Environments (Python 環境)] 節點底下。 以粗體顯示的項目是目前使用中的項目，並且 Visual Studio 使用它來偵錯、匯入和成員完成狀況、語法檢查，以及任何其他需要環境的工作：

![[方案總管] 中顯示的專案環境](media/environments-project.png)

若要為專案啟用不同的環境，請在該環境上按一下滑鼠右鍵，然後選取 [Activate Environment (啟用環境)]。

您可以藉由按一下 [Python Environments (Python 環境)] 並選取 [Add/Remove Python Environments (新增/移除 Python 環境)]，來新增任何全域環境作為專案環境。從顯示的清單中，您可以選取或取消選取專案中可供使用的環境。

![[Add/Remove Python Environments (新增/移除 Python 環境)] 對話方塊](media/environments-add-remove.png)

在 [方案總管] 中，您也可以展開環境來顯示它的已安裝套件 (可供您在環境處於作用中時匯入並在程式碼中使用的套件)：

![[方案總管] 中環境的 Python 套件](media/environments-installed-packages.png)

若要安裝新套件，請在環境上按一下滑鼠右鍵、選取 [Install Python Package (安裝 Python 套件)]，然後輸入所需套件的名稱。 套件 (及相依性) 是下載自 [Python 套件索引 (PyPI) (英文)](https://pypi.python.org/pypi)，您也可以在該處搜尋可用的套件。 Visual Studio 的狀態列和輸出視窗會顯示與該安裝相關的資訊。 若要將套件解除安裝，請在該套件上按一下滑鼠右鍵，然後選取 [移除]。

> [!Note]
> 目前核心 Python 開發小組仍在開發 Python 的套件管理支援。 所顯示的項目可能未必正確，而安裝和解除安裝可能不可靠或可用。 Visual Studio 會使用 pip 套件管理員 (如果可用)，並會在必要時下載並安裝它。 Visual Studio 也可以使用 easy_install 套件管理員。 使用 pip 或 easy_install 從命令列安裝的套件也會一併顯示。

> [!Tip]
> 有一個 pip 無法安裝套件的常見情況，就是當套件的 `*.pyd` 檔案中包含原生元件的原始程式碼時。 如果未安裝所需的 Visual Studio 版本，pip 就無法編譯這些元件。 在此情況下顯示的錯誤訊息是 `error: Unable to find vcvarsall.bat`。 `easy_install` 通常能夠下載預先編譯的二進位檔，而您可以從 [http://aka.ms/VCPython27](http://aka.ms/VCPython27) 下載適用於舊版 Python 的編譯器。 如需詳細資訊，請參閱 Python 工具小組部落格中的[如何處理「找不到 vcvarsallbat」的困擾 (英文)](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/)。

## <a name="virtual-environments"></a>虛擬環境

由於安裝到全域環境中的套件可供使用該環境的所有專案使用，因此當兩個專案所需的套件不相容，或所需的是相同套件的不同版本時，就可能發生衝突。 為了避免這類衝突，Visual Studio 提供建立「虛擬環境」的功能，此環境一般是專案的專屬環境。

與任何其他 Python 環境相同，虛擬環境也是由 Python 解譯器、程式庫及一組套件所組成。 不過，在此情況下，虛擬環境會使用來自其中一個全域環境 (前提是它支援虛擬環境) 的解譯器和程式庫，但其套件則與全域及所有其他虛擬環境分開並隔離。 這項隔離就能避免衝突，並將虛擬環境的資源使用量降到最低來大致符合其套件的大小。 

建立虛擬環境：

1. 在 [方案總管] 中的 [Python Environments (Python 環境)] 上按一下滑鼠右鍵，然後選取 [Add Virtual Environments (新增虛擬環境)]，這會顯示以下畫面：

    ![建立虛擬環境](media/environments-add-virtual-1.png)

1. 指定一個名稱以在您的專案路徑中建立虛擬環境，或是指定一個完整路徑以在其他位置建立它。 (為了確保與其他工具的最大相容性，在名稱中請只使用字母和數字)。

1. 選取一個全域環境來作為基底編譯器，然後按一下 [建立]。 如果沒有 `pip` 和 `virtualenv` 或 `venv` 套件可供使用，就會下載並安裝它們。

    如果提供的路徑是現有的虛擬環境，則會偵測到基底解譯器，而 [建立] 按鈕會變更為 [新增]：

    ![新增現有的虛擬環境](media/environments-add-virtual-2.png)

您同樣可以在 [方案總管] 中的 [Python Environments (Python 環境)] 上按一下滑鼠右鍵，然後選取 [Add Existing Virtual Environment (新增現有的虛擬環境)]，來新增現有的虛擬環境。Visual Studio 會使用環境之 `lib` 目錄中的 `orig-prefix.txt` 檔案來自動偵測基底解譯器。

將虛擬環境新增到您的專案中之後，它會顯示在 [Python Environments (Python 環境)] 視窗中，您可以像啟用任何其他環境一樣啟用它，並且可以管理其套件。 以滑鼠右鍵按一下該環境，然後選取 [移除]，即可移除對該環境的參考，或是刪除該環境及磁碟上它的所有檔案 (但不包括基底編譯器)。

請注意，虛擬機器有一個缺點，就是它們包含硬式編碼檔案路徑，因此無法輕易共用或傳輸到其他開發機器。 幸運的是，您可以使用 `requirements.txt` 檔案，在下一節中將會說明。

## <a name="managing-required-packages"></a>管理必要套件

如果您要將專案與其他人共用、使用建置系統，或是打算[將它發行至 Microsoft Azure](template-azure-cloud-service.md)，則必須指定它所需的外部套件。 建議的方法是使用 [requirements.txt 檔案](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org)，此檔案包含 pip 命令清單，可安裝所需的相依套件版本。

就技術而言，任何檔案名稱都可用來追蹤必要條件 (藉由在安裝套件時使用 `-r <full path to file>`)，但 Visual Studio 為 `requirements.txt` 提供了專屬支援：

- 若您已載入包含 `requirements.txt` 的專案，並想要安裝該檔案中列出的所有套件，請展開**方案總管**中的 [Python 環境] 節點，然後以滑鼠右鍵按一下環境節點，並選取 [從 requirements.txt 安裝]：

    ![Install from requirements.txt (從 requirements.txt 安裝)](media/environments-requirements-txt-install.png)

- 若您已在專案中安裝所有必要套件，可以在方案總管中的環境上按一下滑鼠右鍵，然後選取 [產生 requirements.txt] 以建立必要的檔案。 如果該檔案已經存在，系統會提示您如何更新它：

    ![更新 requirements.txt 選項](media/environments-requirements-txt-replace.png)

  - [Replace entire file (取代整個檔案)] 會移除所有已存在的項目、註解及選項。
  - [重新整理現有項目] 會偵測套件需求並更新版本規範，以符合您目前已安裝的版本。
  - [Update and add entries (更新及新增項目)] 會重新整理所找到的任何需求，並將所有其他套件新增到檔案結尾。

由於 `requirements.txt` 檔案的用意是要固定住您專案的需求，因此所有安裝的套件都已寫明精確的版本。 使用精確的版本可確保您可以在另一部電腦上輕鬆重現您的環境。 即使安裝套件時已指定版本範圍，仍然會包含這些套件作為另一個套件的相依性，或隨附於 pip 以外的安裝程式。

新增虛擬環境時，如果 `requirements.txt` 檔案已經存在，則 [新增虛擬環境] 對話方塊就會顯示自動安裝套件的選項，讓您能夠輕鬆在另一部電腦上重新建立環境：

![使用 requirements.txt 來建立虛擬環境](media/environments-requirements-txt.png)

如果套件是 pip 無法安裝的套件，並且出現在 `requirements.txt` 檔案中，整個安裝就會失敗。 在此情況下，請手動編輯檔案以將此套件排除，或使用 [pip 的選項](http://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format)來參考該套件的可安裝版本。 例如，您可能偏好使用 [`pip wheel`](http://pip.readthedocs.org/en/latest/reference/pip_wheel.html) 來編譯相依性並將 `--find-links <path>` 選項新增到您的 `requirements.txt`：

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="search-paths"></a>搜尋路徑

在典型的 Python 用法中，`PYTHONPATH` 環境變數 (或 `IRONPYTHONPATH` 等) 會提供模組檔案的預設搜尋路徑。 也就是說，當您使用 `import <name>` 陳述式時，Python 會先搜尋其內建模組是否有相符的名稱，接著搜尋包含您要執行之 Python 程式碼的資料夾，然後才搜尋適用的環境變數所定義的「模組搜尋路徑」。 (請參閱核心 Python 文件中的[模組搜尋路徑 (英文)](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) 和[環境變數 (英文)](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH))。

不過，即使針對整個系統設定了搜尋路徑環境變數，Visual Studio 也會將它忽略。 實際上，之所以忽略它，確切說來是「因為」它是針對整個系統設定的，因此會導致產生某些無法自動回答的問題：所參考的模組是用於 Python 2.7 還是 Python 3.3？ 它們是否將覆寫標準程式庫程式庫模組？ 開發人員是否知道此行為，或它是否是惡意的劫持嘗試？

因此，Visual Studio 中的 Python 支援提供一個可在環境和專案中直接指定搜尋路徑的方法。 當您從 Visual Studio 對指令碼進行偵錯或執行指令碼時，搜尋路徑會當作 `PYTHONPATH` (或對等項目) 的值來傳遞。 透過新增搜尋路徑，Visual Studio 便會檢查這些位置中的程式庫，並為它們建置 IntelliSense 資料庫 (視程式庫的數目而定，建構資料庫可能需要一些時間)。

若要新增搜尋路徑，請在 [方案總管] 中的 [Search Paths (搜尋路徑)] 項目上按一下滑鼠右鍵、選取 [Add Folder to Search Path (將資料夾新增到搜尋路徑)]，然後選取要包含的資料夾。 這個路徑會用於與該專案關聯的所有環境。

您也可以新增副檔名為 `.zip` 或 `.egg` 的檔案作為搜尋路徑，方法是選取 [Add Zip Archive to Search Path (將 Zip 封存新增到搜尋路徑)]。與使用資料夾時相同，系統會掃描這些檔案的內容並提供給 IntelliSense 使用。

> [!Note]
> 您可以在使用 Python 3.3 時新增 Python 2.7 模組的搜尋路徑，但結果可能會看到錯誤。

如果您固定使用相同的搜尋路徑且內容不常變更，則將它安裝到您的站台套件資料夾中可能會較有效率。 系統會接著對它進行分析並儲存在 IntelliSense 資料庫中，而且一律會與其預期的環境建立關聯，而您不需要為每個專案新增搜尋路徑。
