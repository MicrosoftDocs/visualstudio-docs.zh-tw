---
title: Python 環境視窗參考
description: 有關 Visual Studio [Python 環境] 視窗中所出現每個索引標籤的詳細資料。
ms.date: 05/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 2e1d894733ee1c8f7de0d45d225f545c2bb59d38
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468582"
---
# <a name="python-environments-window-tabs-reference"></a>Python 環境視窗索引標籤參考

開啟 [Python 環境] 視窗：

- 選取 [檢視] > **[其他視窗]** > **[Python 環境]** 功能表命令。
- 在 [方案總管] 中，以滑鼠右鍵按一下專案的 [Python 環境] 節點，然後選取 [檢視所有 Python 環境]。

如果您將 [Python 環境] 視窗展開至足夠寬度，便會以索引標籤的形式來顯示這些選項，以方便您使用。 為了清楚起見，本文章中的索引標籤會以展開檢視來顯示。

![[Python Environments (Python 環境)] 視窗展開檢視](media/environments-expanded-view.png)

## <a name="overview-tab"></a>Overview (概觀) 索引標籤

提供環境的基本資訊和命令：

![Python 環境的 [Oview (概觀)] 索引標籤](media/environments-overview-tab.png)

| 命令 | 描述 |
| --- | --- |
| **將此環境設為新專案的預設值** | 設定使用中環境，可能會導致在載入 IntelliSense 資料庫時，Visual Studio (2017 15.5 版及更早版本) 短暫沒有反應。 環境如果含有許多套件，則無反應的時間可能會更長。 |
| **瀏覽散發者的網站** | 將瀏覽器開啟至 Python 發行所提供的 URL。 例如，Python 3.x 會移至 python.org。 |
| **開啟互動式視窗** | 在 Visual Studio 內開啟此環境的[互動式 (REPL) 視窗](python-interactive-repl-in-visual-studio.md)，並套用任何[啟動指令碼 (請參閱下面)](#startup-scripts)。 |
| **探索互動式指令碼** | 請參閱[啟動指令碼](#startup-scripts)。 |
| **使用 IPython 互動模式** | 設定時，預設會開啟 IPython 的**互動式**視窗。 這會啟用內嵌繪圖和延伸的 IPython 語法，例如 `name?` 可檢視說明，而 `!command` 適用於殼層命令。 使用需要額外套件的 Anaconda 發佈時，建議使用此選項。 如需詳細資訊，請參閱[在互動式視窗中使用 IPython](interactive-repl-ipython.md)。 |
| **在 PowerShell 中開啟** | 在 PowerShell 命令視窗中啟動解譯器。 |
| (資料夾和程式的連結) | 可讓您快速存取環境的安裝資料夾、*python.exe* 解譯器和 *pythonw.exe* 解譯器。 第一個會在 Windows 檔案總管中開啟，後面兩個則會開啟主控台視窗。 |

### <a name="startup-scripts"></a>啟動指令碼

因為您在日常工作流程中使用互動式視窗，所以您可能會開發定期使用的協助程式函式。 例如，您可以建立可在 Excel 中開啟 DataFrame 的函式，然後將該程式碼儲存為啟動指令碼，讓它一律可在**互動式**視窗中使用。

啟動指令碼包含**互動式**視窗所載入並自動執行的程式碼，包括匯入、函式定義，以及文字形式的任何其他項目。 這類指令碼是使用兩種方式進行參考：

1. 當您安裝環境時，Visual Studio 會建立資料夾 *Documents\Visual Studio 2017\Python Scripts\\\<environment>*，其中的 &lt;environment&gt; 會符合環境的名稱。 您可以使用 [探索互動式指令碼] 命令，輕鬆地巡覽至環境特定資料夾。 當您啟動該環境的**互動式**視窗時，只要依字母順序在這裡找到 *.py* 檔案，就會載入並執行互動式視窗。

1. [工具] > [選項] > **[Python 工具]** > **[互動式視窗]** 索引標籤中的 [指令碼] 控制項 (請參閱[互動式視窗選項](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)) 是用來指定所有環境中載入和執行之啟動指令碼的其他資料夾。 不過，此功能目前無法使用。

## <a name="configure-tab"></a>Configure (設定) 索引標籤

如果有詳細資料，則會包含如下表所述的詳細資料。 如果沒有此索引標籤，即表示目前由 Visual Studio 自動管理所有詳細資料。

![Python 環境的 [Configure (設定)] 索引標籤](media/environments-configure-tab.png)

| 欄位 | 描述 |
| --- | --- |
| **描述** | 要賦予環境的名稱。 |
| **Prefix path (前置路徑)** | 解譯器的基底資料夾位置。 填入此值並按一下 [自動偵測] 之後，Visual Studio 就會嘗試為您填入其他欄位。 |
| **Interpreter path (解譯器路徑)** | 解譯器可執行檔的路徑，通常是前置路徑後面再接著 **python.exe** |
| **Windowed interpreter (Windows 解譯器)** | 非主控台可執行檔的路徑，通常是前置路徑後面再接著 **pythonw.exe**。 |
| **Library path (程式庫路徑)**<br/>(如果有的話) | 指定標準程式庫的根目錄，但如果 Visual Studio 能夠從解譯器要求更精確的路徑，則可以忽略這個值。 |
| **Language version (語言版本)** | 從下拉式功能表中選取。 |
| **架構** | 通常會自動偵測並填入，否則會指定 [32 位元] 或 [64 位元]。 |
| **Path environment variable (路徑環境變數)** | 解譯器用來尋找搜尋路徑的環境變數。 Visual Studio 會在啟動 Python 時變更變數的值，使其包含專案的搜尋路徑。 通常這個屬性應該設定為 **PYTHONPATH**，但有些解譯器會使用不同的值。 |

## <a name="packages-tab"></a>套件索引標籤

在舊版中，也標示為 "pip"。

使用 pip 管理安裝在環境中的套件，讓您也能夠搜尋並安裝新的套件 (包括任何相依性)。 在 Visual Studio 2017 15.7 版及更新版本中，會改為出現使用 Conda 套件管理員的 [套件 (Conda)] 索引標籤。 (如果您沒有看到該選項，請設定 [工具] > [選項] > [Python] > [實驗] > [Use conda package manager when available (instead of pip)] \(可用時使用 Conda 套件管理員 (而不是pip)\) 選項，然後重新啟動 Visual Studio。)

已安裝的套件會和更新 (向上箭頭) 及解除安裝 (位於圓圈中的交叉) 該套件的控制項一起顯示：

![Python 環境套件索引標籤](media/environments-pip-tab-controls.png)

輸入搜尋詞彙能篩選已安裝的套件，以及可從 PyPI 安裝之套件的清單。

![具有針對 "num" 之搜尋的 Python 環境套件索引標籤](media/environments-pip-tab.png)

您可以在上圖中看到，搜尋結果會顯示符合搜尋詞彙的套件數；不過，在清單中的第一個項目，是要直接執行 **pip install \<名稱>** 的命令。 如果您在 [套件 (Conda)] 索引標籤上，您會改為看到 **conda install \<名稱>**：

![顯示 conda install 命令的 Conda 套件索引標籤](media/environments-conda-tab-install.png)

在這兩種情況下，您可以在 [搜尋] 方塊中，在套件名稱之後新增引數來自訂安裝。 包含引數時，搜尋結果會顯示 **pip install** 或 **conda install**，後面接著搜尋方塊的內容：

![使用 pip 和 conda install 命令的引數](media/environments-pip-tab-arguments.png)

安裝套件時會在環境於檔案系統的 *Lib* 資料夾內建立子資料夾。 例如，若您在 *c:\Python36* 中安裝 Python 3.6，套件會安裝在 *c:\Python36\Lib* 中；若您在 *c:\Program Files\Anaconda3* 中安裝 Anaconda3，套件會安裝在 *c:\Program Files\Anaconda3\Lib*。

### <a name="grant-administrator-privileges-for-package-install"></a>授與套件安裝用的系統管理員權限

將套件安裝至位於檔案系統受保護區域的環境時，例如 *c:\Program Files\Anaconda3\Lib*，Visual Studio 必須提高權限來執行 `pip install` 以允許它建立套件子資料夾。 需要提高權限時，Visual Studio 會顯示「可能需要系統管理員權限才可安裝、更新或移除此環境的套件」提示：

![套件安裝的提高權限提示](media/environments-pip-elevate.png)

[立即提高權限] 會將系統管理權限授與 pip 以進行單一作業、主題，也會授與權限的任何作業系統提示。 選取 [在沒有系統管理員權限的情況下繼續] 會嘗試安裝套件，但在嘗試建立包含「錯誤: 無法建立 'C:\Program Files\Anaconda3\Lib\site-packages\png.py': 權限遭拒」這類輸出的資料夾時，pip 會失敗。

選取 [安裝或移除套件時一律提高權限] 可防止在環境有問題時顯示對話方塊。 若要再次顯示對話方塊，請移至 [工具] > [選項] > [Python 工具] > [一般]，然後選取 [重設所有永久隱藏的對話方塊] 按鈕。

在這個相同的 [選項] 索引標籤中，您也可以選取 [一律以系統管理員身分執行 pip] 來隱藏所有環境的對話方塊。 請參閱[選項 - 一般索引標籤](python-support-options-and-settings-in-visual-studio.md#general-options)。

### <a name="security-restrictions-with-older-versions-of-python"></a>較舊版本 Python 的安全性限制

使用 Python 2.6、3.1 和 3.2 時，Visual Studio 會顯示警告「由於新的安全性限制，從網際網路安裝可能不適用於此版本的 Python」：

![較舊版本 Python 的 pip install 限制相關訊息](media/environments-old-version-restriction.png)

警告的原因是，使用這些較舊版本的 Python 時，`pip install` 未包含傳輸安全性層 (TLS) 1.2 的支援，這在從套件來源 pypi.org 下載套件時是必要的。自訂 Python 組建可能會支援 TLS 1.2，在此情況下 `pip install` 可能有效。

可以從 [bootstrap.pypa.io](https://bootstrap.pypa.io/) 下載套件的適當 *get-pip.py*、從 [pypi.org](https://pypi.org/) 手動下載套件，然後從該本機複本安裝套件。

不過，建議直接升級至 Python 2.7 或 3.3+，如此便不會出現警告。

## <a name="intellisense-tab"></a>IntelliSense 索引標籤

顯示 IntelliSense 完成資料庫的目前狀態：

![Python 環境的 [IntelliSense] 索引標籤](media/environments-intellisense-tab.png)

- 在 **Visual Studio 2017 15.5 版**及較舊版本中，IntelliSense 完成取決於已針對該程式庫進行編譯的資料庫。 安裝程式庫時，系統會在背景建置資料庫，但這可能需要花費一些時間，且在您開始撰寫程式碼時可能尚未完成。
- **Visual Studio 2017 15.6 版**及更新版本預設會使用較快速的方法，來在不仰賴資料庫的情況下提供完成。 因此，索引標籤會標示為 [IntelliSense [資料庫已停用]]。 您可以藉由清除 [工具] > [選項] > [Python] > [實驗] > [Use new style IntelliSense for environments] \(在環境中使用新樣式 IntelliSense\) 選項來啟用資料庫。

當 Visual Studio 偵測到新環境 (或您新增環境) 時，會透過分析程式庫原始程式檔來自動開始編譯資料庫。 視所安裝的項目而定，這個程序會花費一分鐘到一小時或數小時不等的時間。 (例如，Anaconda 隨附許多程式庫，因此就需要一些時間來編譯資料庫)。完成之後，您會獲得詳細的 IntelliSense，而在您安裝其他程式庫之前，就不需要再次重新整理資料庫 (使用 [Refresh DB] (重新整理資料庫) 按鈕)。

資料尚未經過編譯的程式庫會標示 **!**；如果環境的資料庫尚未完成，則 **!** 也會出現在主要環境清單中該資料庫的旁邊。

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中管理 Python 環境](managing-python-environments-in-visual-studio.md)
- [選取專案的解譯器](selecting-a-python-environment-for-a-project.md)
- [為相依性使用 requirements.txt](managing-required-packages-with-requirements-txt.md)
- [搜尋路徑](search-paths.md)
