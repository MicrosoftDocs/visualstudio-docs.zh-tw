---
title: "在 Visual Studio 中安裝 Python 支援 | Microsoft Docs"
description: "詳細說明在 Visual Studio 2017、2015、2013、2012 及 2010 中安裝適用於 Visual Studio 的 Python 工具 (PTVS) 的方式，包括可用選項及安裝位置。"
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: a3f788b114b4250819c4867136cb1b888c816cf8
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2018
---
# <a name="installing-python-support-in-visual-studio-on-windows"></a>在 Windows 上的 Visual Studio 中安裝 Python 支援

若要為 Visual Studio 安裝 Python 支援 (也稱為「適用於 Visual Studio 的 Python 工具」或 PTVS)，請遵循符合您 Visual Studio 版本之小節中的指示：

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 和更早版本](#visual-studio-2013-and-earlier)

若為 Visual Studio 2015 和更早版本，也需要另外安裝您所選的 Python 解譯器 (Python 3.5 和更早版本；不支援 3.6 且會產生「不支援的 Python 3.6 版」訊息)。 如需詳細資料，請參閱 [Python 環境](managing-python-environments-in-visual-studio.md)。 相同的頁面也會包含將現有 Python 解譯器新增至 Visual Studio 2017 的指示。

在按照安裝步驟執行之後，若要快速測試 Python 支援，請按 Alt-I 開啟 Python Interactive 視窗，並輸入 `2+2`。 如果您沒有看到 `4` 的輸出，請重新檢查您的步驟。

> [!Tip]
> Python 工作負載包含很有用的 Cookiecutter 擴充功能，能提供探索範本、輸入範本選項，以及建立專案及檔案的圖形化使用者介面。 如需詳細資料，請參閱[使用 Cookiecutter](cookiecutter.md)。

> [!Note]
> 目前在 Visual Studio for Mac 中沒有 Python 支援，但可透過 Visual Studio Code 在 Mac 和 Linux 上取得。 請參閱[問與答](overview-of-python-tools-for-visual-studio.md#questions-and-answers)。

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. 下載並執行最新的 Visual Studio 2017 安裝程式。 您必須安裝 15.2 版或更新版本以使用 Python。

    > [!div class="nextstepaction"]
    > <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">安裝 Visual Studio 2017 Community</a>

    >[!Tip]
    > Community Edition 是針對個別開發人員、課堂學習、學術研究和開放原始碼開發。 針對其他用途，請安裝 <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Professional</a> 或 <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Enterprise</a>。

1. 安裝程式會顯示一份工作負載清單，而工作負載是特定開發區域的相關選項群組。 針對 Python，選取 [Python 開發] 工作負載。

    ![Visual Studio 安裝程式中的 Python 開發工作負載](media/installation-python-workload.png)

    選擇性：如果您要使用資料科學，也請考慮使用 [資料科學與分析應用程式] 工作負載 (Visual Studio 2017 15.2 及更新版本)。 此工作負載支援 Python 以及 R 和 F# 語言。 如需詳細資訊，請參閱[資料科學與分析應用程式工作負載](../rtvs/data-science-workload.md)。

1. 在安裝程式右側，視需要選擇其他選項。 跳過此步驟，以接受預設選項。

    ![Visual Studio 安裝程式中的 Python 開發選項](media/installation-python-options.png)

    | 選項 | 描述 |
    | --- | --- |
    | Python 散發 | 選擇您要使用的 Python 2、Python 3、Anaconda2 和 Anaconda3 散發的任何 32 位元和 64 位元變異組合。 每個都包含散發的解譯器、執行階段和程式庫。 具體而言，Anaconda 是包含各種預先安裝套件的開放型資料科學平台。 (您隨時都可以回到 Visual Studio 安裝程式，以新增或移除散發)。 |
    | Cookiecutter 範本支援 | 安裝 Cookiecutter 圖形化 UI 來探索範本、輸入範本選項，以及建立專案和檔案。 請參閱[使用 Cookiecutter 延伸模組](cookiecutter.md)。 |
    | Python Web 支援 | 安裝進行 Web 開發的工具 (包含 HTML、CSS 和 JavaScript 編輯支援)，以及使用 Bottle、Flask 和 Django 架構之專案的範本。 請參閱 [Python Web 專案範本](template-web.md)。 |
    | Python IoT 支援 | 使用 Python 支援 Windows IoT Core 開發。 |
    | Python 原生開發工具 | 安裝 C++ 編譯器和其他必要元件，以開發 Python 的原生延伸模組。 請參閱[建立適用於 Python 的 C++ 延伸模組](working-with-c-cpp-python-in-visual-studio.md)。 同時也請安裝 [使用 C++ 的桌面開發] 工作負載，以取得完整的 C++ 支援。 |
    | Azure 雲端服務核心工具 | 提供 Python 中 Azure Cloud Services 之開發人員的其他支援。 請參閱 [Azure 雲端服務專案](template-azure-cloud-service.md)。 |

1. 安裝之後，安裝程式會提供選項來修改、啟動、修復或解除安裝 Visual Studio。 任何已安裝元件有更新時，如果 Visual Studio 有更新，則 [修改] 按鈕會變更為 [更新]  (修改選項接著就會出現在下拉式功能表上)。您也可以搜尋 "Visual Studio"，以從 Windows [開始] 功能表啟動 Visual Studio 和安裝程式。

    ![從安裝程式啟動、修改或解除安裝 Visual Studio](media/installation-vs-launch.png)

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567]

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. 從 [控制台] > [程式和功能]，選取 [Microsoft Visual Studio 2015]，再選取 [變更]，以執行 Visual Studio 安裝程式。

1. 在安裝程式中，選取 [修改]。

1. 選取 [程式語言] > [適用於 Visual Studio 的 Python 工具]，然後選取 [下一步]：

    ![Visual Studio 2015 安裝程式中的 PTVS 選項](media/installation-vs2015.png)

1. 當 Visual Studio 安裝完成之後，請[安裝您所選的 Python 解譯器](managing-python-environments-in-visual-studio.md#selecting-and-installing-python-interpreters)。 如果您已安裝解譯器，請參閱[為現有的解譯器建立環境](managing-python-environments-in-visual-studio.md#creating-an-environment-for-an-existing-interpreter)。

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 和更早版本

1. 針對您的 Visual Studio 版本，安裝適當版本的「適用於 Visual Studio 的 Python 工具」：

    - Visual Studio 2013：[適用於 Visual Studio 2013 的 PTVS 2.2 (英文)](https://github.com/Microsoft/PTVS/releases/v2.2)。 Visual Studio 2013 中的 [檔案] > [新增專案] 對話方塊能提供您此程序的捷徑。
    - Visual Studio 2012：[適用於 Visual Studio 2012 的 PTVS 2.1 (英文)](https://pytools.codeplex.com/downloads/get/920478)
    - Visual Studio 2010：[適用於 Visual Studio 2010 的 PTVS 2.1 (英文)](https://pytools.codeplex.com/downloads/get/920479)

1. [安裝您所選的 Python 解譯器](managing-python-environments-in-visual-studio.md#selecting-and-installing-python-interpreters)。 如果您已安裝解譯器，請參閱[為現有的解譯器建立環境](managing-python-environments-in-visual-studio.md#creating-an-environment-for-an-existing-interpreter)。

## <a name="install-locations"></a>安裝位置

根據預設，系統會為電腦上的所有使用者安裝 Python 支援。

針對 Visual Studio 2017，Python 工作負載會安裝在 `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\<VS_edition>Common7\IDE\Extensions\Microsoft\Python`，其中 &lt;VS_edition&gt; 將會是 Community、Professional 或 Enterprise。

針對 Visual Studio 2015 和更早版本，安裝路徑如下：

- 32 位元：
  - 路徑：`%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - 路徑的登錄位置：`HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64 位元︰
  - 路徑：`%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - 路徑的登錄位置：`HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

其中：

- &lt;VS_ver&gt;：
  - 針對 Visual Studio 2015 為 14.0
  - 針對 Visual Studio 2013 為 12.0
  - 針對 Visual Studio 2012 為 11.0
  - 針對 Visual Studio 2010 為 10.0
- &lt;PTVS_ver&gt; 為版本號碼，如 2.2、2.1、2.0、1.5、1.1 或 1.0。

### <a name="user-specific-installations-15-and-earlier"></a>使用者特定安裝 (1.5 和更早版本)

適用於 Visual Studio 1.5 和更早版本的 Python 工具，僅允許針對目前的使用者進行安裝，此情況下的安裝路徑為 `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`，其中 &lt;VS_ver&gt; 和 &lt;PTVS_ver&gt; 的狀況與上述相同。

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
