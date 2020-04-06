---
title: 如何:將擴展性項目遷移到視覺工作室 2017 |微軟文件
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b0cae0261b185ee08400e5f3d25735634663f54a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710985"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>如何:將擴充性項目移到 Visual Studio 2017

本文件介紹如何將擴充性項目升級到 Visual Studio 2017。 除了描述如何更新專案檔外,它還介紹了如何從擴展清單版本 2 (VSIX v2) 升級到新版本 3 VSIX 清單格式 (VSIX v3)。

## <a name="install-visual-studio-2017-with-required-workloads"></a>安裝帶有所需工作負載的可視化工作室 2017

確保您的安裝包括以下工作負載:

* .NET 桌面開發
* Visual Studio 擴充功能開發

## <a name="open-vsix-solution-in-visual-studio-2017"></a>2017年在視覺工作室開放 VSIX 解決方案

所有 VSIX 專案都需要將主要版本單向升級到 Visual Studio 2017。

專案檔(例如 =*.csproj)* 將更新:

* 最小視覺工作室版本 - 現在設定為 15.0
* 舊工具版本(如果以前存在) ─ 現在設定為 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>更新 Microsoft.VSSDK.BuildTools NuGet 套件

> [!Note]
> 如果您的解決方案不引用 Microsoft.VSSDK.BuildTools NuGet 包,您可以跳過此步驟。

為了以新的 VSIX v3(版本 3)格式建置擴展,需要使用新的 VSSDK 構建工具建構解決方案。 這將與 Visual Studio 2017 一起安裝,但您的 VSIX v2 擴展可能透過 NuGet 保留對舊版本的引用。 如果是這樣,您需要手動安裝 Microsoft.VSSDK.BuildTools NuGet 包的更新。

要更新對 Microsoft.VSSDK.BuildTools 的 NuGet 引用,

* 右鍵單擊解決方案,然後選擇 **「管理 NuGet 包以用於解決方案**」。
* 導覽**到 "更新**"選項卡。
* 選擇**微軟.VSSDK.BuildTools(最新版本)**.
* 按**更新**。

![VSSDK 建置工具](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>變更 VSIX 延伸清單

為了確保使用者安裝 Visual Studio 具有執行擴展所需的所有程式集,請在擴展清單檔中指定所有先決條件元件或包。 當用戶嘗試安裝擴展時,VSIX安裝程式將檢查是否安裝了所有先決條件。 如果缺少某些元件,系統將提示使用者安裝缺少的元件,作為擴展安裝過程的一部分。

> [!Note]
> 至少,所有擴展都應指定 Visual Studio 核心編輯器元件作為先決條件。

* 編輯副檔(通常稱為*source.擴展.vsixmanifest)。*
* 確保`InstallationTarget`包含15.0。
* 添加所需的安裝先決條件(如下例所示)。
  * 我們建議您僅為安裝先決條件指定元件指示。
  * 有關[識別元件標識](#find-component-ids)的說明,請參閱本文檔末尾的部分。

範例：

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>選項:使用設計器對 VSIX 擴充清單進行變更

您可以使用清單設計器中的新**先決條件**選項卡來選擇先決條件,並將為您更新 XML,而不是直接編輯清單 XML。

> [!Note]
> 清單設計器僅允許您選擇當前 Visual Studio 實例上安裝的元件(不是工作負載或包)。 如果需要為當前未安裝的工作負荷、包或元件添加先決條件,請直接編輯清單 XML。

* *開源.擴展.vsixmanifest [設計]* 檔案。
* 選擇 **「先決條件」** 選項卡,然後按 **「新建」** 按鈕。

   ![VSIX 清單設計器](media/vsix-manifest-designer.png)

* 將打開 **「添加新先決條件」** 視窗。

   ![新增 v6 先決條件](media/add-vsix-prerequisite.png)

* 按下 **「名稱」** 的下拉清單並選擇所需的先決條件。
* 如有必要,請更新版本。

   > [!Note]
   > 版本欄位將預填充當前安裝的元件的版本,其範圍範圍將不超過(但不包括)元件的下一個主要版本。

   ![新增羅斯林先決條件](media/add-roslyn-prerequisite.png)

* 按下 **[確定]**。

## <a name="update-debug-settings-for-the-project"></a>更新項目的除錯設定

如果要在 Visual Studio 的實驗實例中調試擴展,請確保**除錯** > **開始操作**的專案設定具有 **「開始」外部程式:** 值設定為 Visual Studio 2017 安裝的*devenv.exe*檔。

它可能看起來像: *C:_程式檔 (x86)\微軟可視化工作室\2017_企業_Common7_IDE_devenv.exe*

![啟動外部程式](media/start-external-program.png)

> [!Note]
> 除錯啟動操作通常儲存在 *.csproj.user*檔中。 此檔通常包含在 *.gitignore*檔中,因此,當提交到原始程式碼管理時,通常不會與其他專案檔一起保存。 因此,如果您剛剛從原始程式碼管理中拉出解決方案,則專案很可能沒有為"開始操作"設置任何值。 使用 Visual Studio 2017 創建的新 VSIX 專案將建立一個 *.csproj.user*檔案,預設指向當前 Visual Studio 安裝目錄。 但是,如果要遷移 VSIX v2 副檔名,*則 .csproj.user*檔案可能包含對以前 Visual Studio 版本的安裝目錄的引用。 設置**調試** > **啟動操作**的值將允許在嘗試調試擴展時啟動正確的 Visual Studio 實驗實例。

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>檢查延伸是否正確產生 (作為 VSIX v3)

* 構建 VSIX 專案。
* 解壓縮生成的 VSIX。
  * 預設情況下,VSIX 檔案位於*bin/除錯*或*bin/釋放*中,作為 *[您的自訂擴展]vsix*。
  * 將 *.vsix*重新命名為 *.zip,* 以便輕鬆查看內容。
* 檢查是否存在三個檔:
  * *延伸.vsix清單*
  * *清單.json*
  * *目錄.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>檢查何時安裝所有必要的先決條件

測試 VSIX 是否成功安裝在安裝了所有必需先決條件的電腦上。

> [!Note]
> 在安裝任何擴展之前,請關閉 Visual Studio 的所有實例。

試著安裝延伸:

* 在視覺工作室 2017

![Visual Studio 2017 上的 VSIX 安裝程式](media/vsixinstaller-vs-2017.png)

* 可選:檢查早期版本的可視化工作室。
  * 證明向後相容性。
  * 應適用於 Visual Studio 2012, 視覺工作室 2013, 視覺工作室 2015.
* 可選:檢查 VSIX 安裝程式版本檢查器提供版本選擇。
  * 包括早期版本的可視化工作室(如果已安裝)。
  * 包括視覺工作室 2017.

如果最近打開了 Visual Studio,您可能會看到如下所示的對話方塊:

![與正在執行的程序](media/vs-running-processes.png)

等待行程關閉或手動結束任務。 您可以按列出的名稱查找進程,也可以在括弧中列出 PID。

> [!Note]
> 在運行 Visual Studio 實例時,這些進程不會自動關閉。 確保已關閉電腦上的所有 Visual Studio 實例,包括其他使用者的實例,然後繼續重試。

## <a name="check-when-missing-the-required-prerequisites"></a>檢查何時缺少所需的先決條件

* 嘗試在具有 Visual Studio 2017 的電腦上安裝擴展,該電腦不包含先決條件中定義的所有元件(上圖)。
* 檢查安裝標識缺少的元件,並將其列為 VSIX 安裝程式的先決條件。
* 注意:如果需要隨擴展一起安裝任何先決條件,則需要提升。

![vsix安裝程式缺少先決條件](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>決定元件

尋找依賴項時,您會發現一個依賴項可以映射到多個元件。 為了確定應指定哪些依賴項作為先決條件,我們建議您選擇具有與擴展類似的功能的元件,並考慮您的使用者以及他們最有可能安裝或不介意安裝的元件類型。 我們還建議構建擴展,使所需的先決條件僅滿足允許擴展運行的最小值,並且如果沒有檢測到某些元件,則其他功能的擴展將處於休眠狀態。

為了提供進一步的指導,我們確定了一些常見的擴展類型及其建議的先決條件:

擴充功能類型 | 顯示名稱 | ID
--- | --- | ---
編輯器 | Visual Studio 核心編輯器 | Microsoft.VisualStudio.Component.CoreEditor
羅斯林 | C# 和 Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Managed 桌面工作負載核心 | Microsoft.VisualStudio.Component.ManagedDesktop.Core
偵錯工具 | Just-in-Time 偵錯工具 | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>尋找元件指示

Visual Studio 產品排序的元件清單位於[Visual Studio 2017 工作負載和元件 IT。](/visualstudio/install/workload-and-component-ids?view=vs-2019) 將這些元件的代號用於清單中的先決條件。

如果您不確定哪個元件包含特定的二進位檔案,請下載元件[-> 二進制映射電子表格](https://aka.ms/vs2017componentid-binaries)。

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-元件二進位對應.xlsx

Excel 工作表中有四列:**元件名稱**、元件**Id、****版本**與**二進位/檔案名稱**。  您可以使用篩選器來搜尋和尋找特定的元件和二進位檔案。

對於所有引用,請先確定哪些引用位於核心編輯器(Microsoft.VisualStudio.元件.核心編輯器)元件中。  至少,我們需要將核心編輯器元件指定為所有擴展的先決條件。 在不在核心編輯器中留下的引用中,在 **「二進位/檔案名稱**」部分中添加篩選器,以查找具有這些引用任何子集的元件。

範例：

* 如果您有調試器副檔名,並且知道專案具有*VSDebugEng.dll*和*VSDebug.dll*的引用,請按下 **"二進位/檔名稱**"標題中的篩選器按鈕。  搜尋"VSDebugEng.dll"並選擇 *「確定*」。  接下來,再次按下 **「二進位/檔名稱**」標題中的篩選器按鈕,然後搜索「VSDebug.dll」。。  選擇選擇選擇**選擇所選取的欄位 「****選擇」 。**  現在瀏覽**元件名稱**,尋找與您的擴充類型最相關的元件。 在此範例中,您將選擇「準時調試器」並將其添加到 vsixmanifest 中。
* 如果您知道專案涉及調試器元素,則可以在篩選器搜索框中搜索「調試器」以查看哪些元件在其名稱中包含調試器。

## <a name="specify-a-visual-studio-2017-release"></a>指定視覺工作室 2017 版本

例如,如果擴展需要 Visual Studio 2017 的特定版本,則它取決於 15.3 中發布的功能,則必須在 VSIX**安裝目標**中指定內部版本號。 例如,版本 15.3 的生成號為"15.0.26730.3"。 你可以[在這裡](../install/visual-studio-build-numbers-and-release-dates.md)看到版本映射以生成數位。 使用版本號「15.3」將不能正常工作。

如果您的延伸需要 15.3 或更高版本,您將聲明**安裝目標版本**為 [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
