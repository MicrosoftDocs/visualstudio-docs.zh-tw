---
title: 將擴充性專案移轉至 Visual Studio 2017
titleSuffix: ''
description: 瞭解如何將擴充性專案升級為 Visual Studio 2017，以及如何從擴充功能資訊清單第2版升級至第3版 VSIX 資訊清單。
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 58d802ad97018a3d84e2b6a9f5e759db3a7cb2e3
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993961"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>如何：將擴充性專案遷移至 Visual Studio 2017

本檔說明如何將擴充性專案升級為 Visual Studio 2017。 除了描述如何更新專案檔之外，也會說明如何從擴充資訊清單第2版 (VSIX v2) 升級為新的版本 3 VSIX 資訊清單格式 (VSIX v3) 。

## <a name="install-visual-studio-2017-with-required-workloads"></a>使用必要的工作負載安裝 Visual Studio 2017

請確定您的安裝包含下列工作負載：

* .NET 桌面開發
* Visual Studio 擴充功能開發

## <a name="open-vsix-solution-in-visual-studio-2017"></a>在 Visual Studio 2017 中開啟 VSIX 方案

所有 VSIX 專案都需要主要版本的單向升級至 Visual Studio 2017。

專案檔案 (例如 **.csproj*) 將會更新：

* MinimumVisualStudioVersion-現在設定為15。0
* OldToolsVersion (如果先前存在) -現在設定為14。0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>更新 VSSDK. BuildTools NuGet 套件

> [!Note]
> 如果您的解決方案未參考 VSSDK. BuildTools NuGet 套件，則可以略過此步驟。

若要以新的 VSIX v3 (第3版) 格式來建立擴充功能，您的解決方案必須使用新的 VSSDK Build Tools 建立。 這會隨 Visual Studio 2017 一起安裝，但您的 VSIX v2 延伸模組可能會透過 NuGet 保留較舊版本的參考。 若是如此，您將需要為您的解決方案手動安裝 VSSDK BuildTools NuGet 套件的更新。

若要將 NuGet 參考更新至 VSSDK. BuildTools：

* 以滑鼠右鍵按一下方案，然後選擇 [ **管理方案的 NuGet 套件**]。
* 流覽至 [ **更新** ] 索引標籤。
* 選取 [ **VSSDK])  (最新版本**。
* 按下 [ **更新**]。

![VSSDK build tools](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>對 VSIX 擴充功能資訊清單進行變更

為確保使用者的 Visual Studio 安裝具有執行擴充功能所需的所有元件，請在擴充功能資訊清單檔案中指定所有必要條件元件或套件。 當使用者嘗試安裝此延伸模組時，VSIXInstaller 會檢查是否已安裝所有必要條件。 如果缺少某些元件，系統會提示使用者安裝遺失的元件，做為延伸模組安裝程式的一部分。

> [!Note]
> 所有擴充功能至少都應該將 Visual Studio 核心編輯器元件指定為必要條件。

* 編輯延伸模組資訊清單檔 (通常稱為 *extension.vsixmanifest*) 。
* 請確定 `InstallationTarget` 包含15.0。
* 新增必要的安裝必要條件 (，如下列範例所示) 。
  * 建議您僅針對安裝必要條件指定元件識別碼。
  * 如需 [識別元件識別碼的指示](#find-component-ids)，請參閱本檔結尾的一節。

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>選項：使用設計工具來變更 VSIX 擴充功能資訊清單

您可以使用資訊清單設計工具中的 [新增 **必要條件** ] 索引標籤來選取必要條件，並為您更新 XML，而不需要直接編輯資訊清單 XML。

> [!Note]
> 資訊清單設計工具只會讓您選取 (非目前 Visual Studio 實例上所安裝之工作負載或封裝) 的元件。 如果您需要為目前未安裝的工作負載、封裝或元件新增先決條件，請直接編輯資訊清單 XML。

* *Extension.vsixmanifest [Design]* 檔案的開放原始碼。
* 選取 [ **必要條件** ] 索引標籤，然後按 [ **新增** ] 按鈕。

   ![VSIX 資訊清單設計工具](media/vsix-manifest-designer.png)

* [ **新增** 必要條件] 視窗隨即開啟。

   ![新增 vsix 先決條件](media/add-vsix-prerequisite.png)

* 按一下 [ **名稱** ] 下拉式清單，然後選取所需的先決條件。
* 如有必要，請更新版本。

   > [!Note]
   > [版本] 欄位將會預先填入目前安裝的元件版本，其範圍最多可 (但不包括) 元件的下一個主要版本。

   ![新增 roslyn 先決條件](media/add-roslyn-prerequisite.png)

* 按下 **[確定]**。

## <a name="update-debug-settings-for-the-project"></a>更新專案的偵錯工具設定

如果您想要在 Visual Studio 的實驗實例中，對您的擴充功能進行偵錯工具，請確定 **debug**  >  **啟動動作** 的專案設定具有 [**啟動外部程式：** 值] 設定為 Visual Studio 2017 安裝的 *devenv.exe* 檔案。

它可能看起來像： *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![啟動外部程式](media/start-external-program.png)

> [!Note]
> Debug 開始動作通常會儲存在 *.csproj. 使用者* 檔案中。 這個檔案通常會包含在 *.gitignore* 檔案中，因此，在認可至原始檔控制時，通常不會與其他專案檔一起儲存。 因此，如果您從原始檔控制提取您的方案，則專案可能不會針對 [開始] 動作設定任何值。 使用 Visual Studio 2017 建立的新 VSIX 專案，將會有以預設值指向目前 Visual Studio 安裝目錄的 *.csproj. 使用者檔案。* 但是，如果您要遷移 VSIX v2 延伸模組，則 *.csproj. 使用者* 檔案可能會包含先前 Visual Studio 版本之安裝目錄的參考。 當您嘗試對延伸模組進行偵錯工具時，將值設定為 [ **Debug**  >  **Start action** ] 將會允許正確的 Visual Studio 實驗實例啟動。

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>檢查延伸模組是否已正確建立 (為 VSIX v3) 

* 建立 VSIX 專案。
* 將產生的 VSIX 解壓縮。
  * 根據預設，VSIX 檔案存在於 *bin/Debug* 或 *bin/Release* 中為 *[YourCustomExtension] .vsix*。
  * 將 *.vsix* 重新命名為 *.zip* 可輕鬆地查看內容。
* 檢查是否有三個檔案：
  * *extension.vsixmanifest*
  * *manifest.js開啟*
  * *catalog.js開啟*

## <a name="check-when-all-required-prerequisites-are-installed"></a>檢查是否已安裝所有必要的必要條件

測試 VSIX 是否已安裝在已安裝所有必要必要條件的電腦上。

> [!Note]
> 安裝任何延伸模組之前，請關閉 Visual Studio 的所有實例。

嘗試安裝此延伸模組：

* 在 Visual Studio 2017

![Visual Studio 2017 上的 VSIX 安裝程式](media/vsixinstaller-vs-2017.png)

* 選用：檢查舊版 Visual Studio。
  * 證明回溯相容性。
  * 適用于 Visual Studio 2012、Visual Studio 2013 Visual Studio 2015。
* 選擇性：檢查 VSIX 安裝程式版本檢查程式是否提供版本的選項。
  * 包含舊版 Visual Studio (（如果已安裝) ）。
  * 包含 Visual Studio 2017。

如果 Visual Studio 最近開啟，您可能會看到如下所示的對話方塊：

![vs 正在執行的進程](media/vs-running-processes.png)

等候進程關機，或手動結束工作。 您可以依列出的名稱或在括弧中列出的 PID 來尋找處理常式。

> [!Note]
> 當 Visual Studio 的實例正在執行時，這些處理常式將不會自動關閉。 確定您已關閉電腦上 Visual Studio 的所有實例（包括來自其他使用者的實例），然後繼續重試。

## <a name="check-when-missing-the-required-prerequisites"></a>檢查缺少必要必要條件的情況

* 嘗試在 Visual Studio 2017 的電腦上安裝延伸模組，但該電腦未包含上述必要條件 (中所定義的所有元件) 。
* 檢查安裝是否可識別遺失的元件，並將它們列為 VSIXInstaller 中的必要條件。
* 注意：如果任何必要條件需要隨副檔名一起安裝，就需要提高許可權。

![vsixinstaller 缺少必要元件](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>決定元件

查閱您的相依性時，您會發現其中一個相依性可能對應至多個元件。 若要判斷您的必要條件應指定的相依性，我們建議您選擇具有類似您延伸模組的功能，並同時考慮您的使用者，以及他們最可能安裝或不介意安裝的元件類型。 此外，我們也建議您以所需的先決條件來建立您的延伸模組，讓您的延伸模組能夠執行，而且如果未偵測到某些元件，則會讓其他功能處於休眠狀態。

為了提供進一步的指引，我們已識別出幾種常見的延伸模組類型和其建議的必要條件：

擴充功能類型 | 顯示名稱 | 識別碼
--- | --- | ---
編輯器 | Visual Studio 核心編輯器 | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# 和 Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Managed 桌面工作負載核心 | Microsoft.VisualStudio.Component.ManagedDesktop.Core
偵錯工具 | Just-in-Time 偵錯工具 | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>尋找元件識別碼

依 Visual Studio 產品排序的元件清單是在 [2017 工作負載和元件識別碼 Visual Studio](../install/workload-and-component-ids.md?view=vs-2019&preserve-view=true)。 針對您的資訊清單中的必要條件識別碼使用這些元件識別碼。

如果您不確定哪個元件包含特定的二進位檔，請下載 [元件 > 的二進位對應試算表](https://aka.ms/vs2017componentid-binaries)。

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Excel 工作表中有四個數據行： [元件名稱]、[**元件名稱** **]、[****版本**] 和 [**二進位/檔案名**]。  您可以使用篩選準則來搜尋和尋找特定的元件和二進位檔。

針對您所有的參考，請先判斷哪些是在核心編輯器中的 (VisualStudio) 元件。  我們至少需要將核心編輯器元件指定為所有延伸模組的必要條件。 對於不在核心編輯器中的參考，請在 [ **二進位檔/檔案名** ] 區段中加入篩選，以尋找具有這些參考子集的元件。

範例：

* 如果您有偵錯工具擴充功能，並且知道您的專案具有 *VSDebugEng.dll* 和 *VSDebug.dll* 的參考，請按一下 [ **二進位檔/檔案名** ] 標頭中的 [篩選] 按鈕。  搜尋 "VSDebugEng.dll"，然後選取 *[確定]*。  接著再按一下 [ **二進位檔/檔案名** ] 標頭中的 [篩選] 按鈕，然後搜尋 "VSDebug.dll"。  選取 [ **加入目前選取範圍來篩選** ] 核取方塊，然後選取 **[確定]**。  現在查看 **元件名稱** ，以尋找與您的延伸模組類型最相關的元件。 在此範例中，您會選擇即時偵錯工具，並將它新增至您的 extension.vsixmanifest。
* 如果您知道您的專案會處理偵錯工具元素，您可以在篩選搜尋方塊中搜尋「偵錯工具」，以查看其名稱中包含偵錯工具的元件。

## <a name="specify-a-visual-studio-2017-release"></a>指定 Visual Studio 2017 版本

例如，如果您的延伸模組需要特定版本的 Visual Studio 2017 （例如，它取決於在15.3 中發行的功能），您必須在 VSIX **InstallationTarget** 中指定組建編號。 例如，版本15.3 的組建編號為 ' 15.0.26730.3 '。 您可以在 [這裡](../install/visual-studio-build-numbers-and-release-dates.md)看到版本與組建編號的對應。 使用版本號碼 ' 15.3 ' 將無法正常運作。

如果您的延伸模組需要15.3 或更高版本，您會將 **InstallationTarget 版本** 宣告為 [15.0.26730.3，16.0) ：

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```