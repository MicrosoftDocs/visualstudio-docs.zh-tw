---
title: 安裝 Python 支援
description: 如何在 Visual Studio 2017、2015、2013、2012 和 2010 中安裝「適用於 Visual Studio 的 Python 工具」(PTVS)，包括選項和安裝位置。
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e0c1cf29c7579978d5992de46b14c01fee0799c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881642"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>如何在 Windows 上的 Visual Studio 中安裝 Python 支援

若要為 Visual Studio 安裝 Python 支援 (也稱為「適用於 Visual Studio 的 Python 工具」或 PTVS)，請遵循符合您 Visual Studio 版本之小節中的指示：

- [Visual Studio 2017 和 Visual Studio 2019](#visual-studio-2017-and-2019)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 和更早版本](#visual-studio-2013-and-earlier)

在按照安裝步驟執行之後，若要快速測試 Python 支援，請按 **Alt**+**I** 並輸入 `2+2`開啟 [Python 互動式] 視窗。 如果您沒有看到 `4` 的輸出，請重新檢查您的步驟。

> [!Tip]
> Python 工作負載包含很有用的 Cookiecutter 擴充功能，能提供探索範本、輸入範本選項，以及建立專案及檔案的圖形化使用者介面。 如需詳細資料，請參閱[使用 Cookiecutter](using-python-cookiecutter-templates.md)。

> [!Note]
> 目前在 Visual Studio for Mac 中沒有 Python 支援，但可透過 Visual Studio Code 在 Mac 和 Linux 上取得。 查看 [問題和解答](overview-of-python-tools-for-visual-studio.md#questions-and-answers)。

<a name="visual-studio-2017-and-2019"></a>
## <a name="visual-studio-2019-and-visual-studio-2017"></a>Visual Studio 2019 和 Visual Studio 2017

1. 下載並執行最新的 Visual Studio 安裝程式。 如果您已經安裝 Visual Studio，請執行 Visual Studio 安裝程式、選取 [修改] 選項 (請參閱[修改 Visual Studio](../install/modify-visual-studio.md)) 並移至步驟 2。

    > [!div class="nextstepaction"]
    > [安裝 Visual Studio 2019 社區](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Community Edition 是針對個別開發人員、課堂學習、學術研究和開放原始碼開發。 針對其他用途，請安裝 [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) 或 [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)。

1. 安裝程式會顯示一份工作負載清單，而工作負載是特定開發區域的相關選項群組。 針對 Python，選取 [Python 開發] 工作負載。

    ![Visual Studio 安裝程式中的 Python 開發工作負載](media/installation-python-workload.png)

    ::: moniker range="vs-2017"
    選擇性：如果您要使用資料科學，也請考慮 [資料科學與分析應用程式] 工作負載。 此工作負載支援 Python、R 以及 F# 語言。 如需詳細資訊，請參閱[資料科學與分析應用程式工作負載](data-science-and-analytical-applications-workload.md)。

    > [!Note]
    > 只有 Visual Studio 2017 15.2 版和更新版本才提供 Python 和「資料科學」工作負載。

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    選擇性：如果您要使用資料科學，也請考慮 [資料科學與分析應用程式] 工作負載。 此工作負載支援 Python 以及 F# 語言。 如需詳細資訊，請參閱[資料科學與分析應用程式工作負載](data-science-and-analytical-applications-workload.md)。
    ::: moniker-end

1. 在安裝程式右側，視需要選擇其他選項。 跳過此步驟，以接受預設選項。

    ::: moniker range="vs-2017"
    ![Visual Studio 安裝程式中的 Python 開發選項](media/installation-python-options.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    ![Visual Studio 2019 安裝程式中的 Python 開發選項](media/installation-python-options-2019.png)
    ::: moniker-end

    ::: moniker range="<=vs-2017"
    | 選項 | Description |
    | --- | --- |
    | Python 散發 | 選擇任何可用選項的組合，例如您計劃使用的 Python 2、Python 3、Miniconda、Anaconda2 和 Anaconda3 散發的任何 32 位元和 64 位元變異組合。 每個都包含散發的解譯器、執行階段和程式庫。 具體而言，Anaconda 是包含各種預先安裝套件的開放型資料科學平台。  (您隨時都可返回 Visual Studio 安裝程式來新增或移除散發套件。 )  **注意**：如果您已在 Visual Studio 安裝程式之外安裝發佈，就不需要在此檢查對應的選項。 Visual Studio 會自動偵測現有的 Python 安裝。 請參閱 [Python 環境視窗](managing-python-environments-in-visual-studio.md#the-python-environments-window)。 此外，如果已提供比安裝程式中所示還要新的 Python 版本，您可以另外安裝該版本，而且 Visual Studio 將會偵測到該版本。 |
    | **Cookiecutter 範本支援** | 安裝 Cookiecutter 圖形化 UI 來探索範本、輸入範本選項，以及建立專案和檔案。 請參閱[使用 Cookiecutter 延伸模組](using-python-cookiecutter-templates.md)。 |
    | **Python Web 支援** | 安裝進行 Web 開發的工具 (包含 HTML、CSS 和 JavaScript 編輯支援)，以及使用 Bottle、Flask 和 Django 架構之專案的範本。 請參閱 [Python Web 專案範本](python-web-application-project-templates.md)。 |
    | **Python IoT 支援** | 使用 Python 支援 Windows IoT Core 開發。 |
    | **Python 原生開發工具** | 安裝 C++ 編譯器和其他必要元件，以開發 Python 的原生延伸模組。 請參閱[建立適用於 Python 的 C++ 延伸模組](working-with-c-cpp-python-in-visual-studio.md)。 同時也請安裝 [使用 C++ 的桌面開發] 工作負載，以取得完整的 C++ 支援。 |
    | **Azure 雲端服務核心工具** | 提供 Python 中 Azure Cloud Services 之開發人員的其他支援。 請參閱 [Azure 雲端服務專案](python-azure-cloud-service-project-template.md)。 |
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    | 選項 | Description |
    | --- | --- |
    | Python 散發 | 選擇任何可用選項的組合，例如您計劃使用的 Python 2、Python 3、Miniconda、Anaconda2 和 Anaconda3 散發的任何 32 位元和 64 位元變異組合。 每個都包含散發的解譯器、執行階段和程式庫。 具體而言，Anaconda 是包含各種預先安裝套件的開放型資料科學平台。  (您隨時都可返回 Visual Studio 安裝程式來新增或移除散發套件。 )  **注意**：如果您已在 Visual Studio 安裝程式之外安裝發佈，就不需要在此檢查對應的選項。 Visual Studio 會自動偵測現有的 Python 安裝。 請參閱 [Python 環境視窗](managing-python-environments-in-visual-studio.md#the-python-environments-window)。 此外，如果已提供比安裝程式中所示還要新的 Python 版本，您可以另外安裝該版本，而且 Visual Studio 將會偵測到該版本。 |
    | **Cookiecutter 範本支援** | 安裝 Cookiecutter 圖形化 UI 來探索範本、輸入範本選項，以及建立專案和檔案。 請參閱[使用 Cookiecutter 延伸模組](using-python-cookiecutter-templates.md)。 |
    | **Python Web 支援** | 安裝進行 Web 開發的工具 (包含 HTML、CSS 和 JavaScript 編輯支援)，以及使用 Bottle、Flask 和 Django 架構之專案的範本。 請參閱 [Python Web 專案範本](python-web-application-project-templates.md)。 |
    | **Python 原生開發工具** | 安裝 C++ 編譯器和其他必要元件，以開發 Python 的原生延伸模組。 請參閱[建立適用於 Python 的 C++ 延伸模組](working-with-c-cpp-python-in-visual-studio.md)。 同時也請安裝 [使用 C++ 的桌面開發] 工作負載，以取得完整的 C++ 支援。 |
    | **Azure 雲端服務核心工具** | 提供 Python 中 Azure Cloud Services 之開發人員的其他支援。 請參閱 [Azure 雲端服務專案](python-azure-cloud-service-project-template.md)。 |
    ::: moniker-end

1. 安裝之後，安裝程式會提供選項來修改、啟動、修復或解除安裝 Visual Studio。 任何已安裝元件有 Visual Studio 的更新時，[修改] 按鈕會變更為 [更新]。  ([ **修改** ] 選項接著就會出現在下拉式功能表中 ) 。您也可以從 Windows [ **開始** ] 功能表中搜尋「Visual Studio」來啟動 Visual Studio 和安裝程式。

    ![從安裝程式啟動、修改或解除安裝 Visual Studio](media/installation-vs-launch.png)

### <a name="troubleshooting"></a>疑難排解

如果您在於 Visual Studio 中安裝或執行 Python 時發生問題，請嘗試下列操作：

- 使用 Python CLI (也就是從命令提示字元執行 *python.exe*) 來判斷是否會發生相同錯誤。
- 使用 Visual Studio 安裝程式中的 [ [**修復**](../install/repair-visual-studio.md) ] 選項。
- 透過  >  Windows 中的設定 **應用程式 & 功能** 來修復或重新安裝 Python。

**範例錯誤**：無法啟動互動式處理序: System.ComponentModel.Win32Exception (0x80004005): 在 Microsoft.PythonTools.Repl.PythonInteractiveEvaluator.d__43.MoveNext() 發生未知的錯誤 (0xc0000135)。

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. 從 [控制台] > [程式和功能]，選取 [Microsoft Visual Studio 2015]，再選取 [變更]，以執行 Visual Studio 安裝程式。

1. 在安裝程式中，選取 [修改]。

1. 選取程式 **設計語言**  >  **適用於 Visual Studio 的 Python 工具** 然後 **下一步**：

    ![Visual Studio 2015 安裝程式中的 PTVS 選項](media/installation-vs2015.png)

1. 當 Visual Studio 安裝完成之後，請[安裝您所選的 Python 解譯器](installing-python-interpreters.md)。 Visual Studio 2015 僅支援 Python 3.5 和更早版本，較新的版本會產生類似「不支援的 Python 3.6 版」的訊息。 如果您已安裝解譯器但 Visual Studio 無法自動偵測到該解譯器，請參閱[手動識別現有的環境](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)。

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 和更早版本

1. 針對您的 Visual Studio 版本，安裝適當版本的「適用於 Visual Studio 的 Python 工具」：

    - Visual Studio 2013： [PTVS 2.2.2 for Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2.2)。 Visual Studio 2013 中 **的 [** 檔案  >  **新增專案**] 對話方塊會提供此程式的快捷方式。
    - Visual Studio 2010 和2012： [PTVS 2.1.1 Visual Studio 2010 和 2012](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [安裝您所選的 Python 解譯器](installing-python-interpreters.md)。 如果您已安裝解譯器但 Visual Studio 無法自動偵測到該解譯器，請參閱[手動識別現有的環境](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)。

## <a name="install-locations"></a>安裝位置

根據預設，系統會為電腦上的所有使用者安裝 Python 支援。

針對 Visual Studio 2019 和 Visual Studio 2017，Python 工作負載會安裝在 *%ProgramFiles(x86)%\Microsoft Visual Studio\\<VS_version>\\<VS_edition>Common7\IDE\Extensions\Microsoft\Python*，其中 &lt;VS_version&gt; 是 2019 或 2017，&lt;VS_edition&gt; 是 Community、Professional 或 Enterprise。

針對 Visual Studio 2015 和更早版本，安裝路徑如下：

- 32 位元：
  - 路徑： *% Program Files (x86) % \ Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio \\<* PTVS_ver
  - 路徑的登錄位置：**HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\<VS_ver>\InstallDir**
- 64 位元︰
  - 路徑： *% Program Files%\Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio \\<PTVS_ver>*
  - 路徑的登錄位置：**HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\<VS_ver>\InstallDir**

其中：

- &lt;VS_ver&gt;：
  - 針對 Visual Studio 2015 為 14.0
  - 針對 Visual Studio 2013 為 12.0
  - 針對 Visual Studio 2012 為 11.0
  - 針對 Visual Studio 2010 為 10.0
- &lt;PTVS_ver &gt; 是版本號碼，例如2.2.2、2.1.1、2.0、1.5、1.1 或1.0。

### <a name="user-specific-installations-15-and-earlier"></a>使用者特定安裝 (1.5 和更早版本)

適用於 Visual Studio 1.5 和更早版本的 Python 工具，僅允許針對目前的使用者進行安裝，此情況下的安裝路徑為 *%LocalAppData%\Microsoft\VisualStudio\\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\\<PTVS_ver>*，其中 &lt;VS_ver&gt; 和 &lt;PTVS_ver&gt; 的狀況與上述相同。
