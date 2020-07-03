---
title: 如何：將擴充性專案遷移至 Visual Studio 2017 |Microsoft Docs
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 37f7259c1133ea51e004b5f6b2061427ff71dea0
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905839"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>如何：將擴充性專案遷移至 Visual Studio 2017

本檔說明如何將擴充性專案升級至 Visual Studio 2017。 除了描述如何更新專案檔之外，它也會說明如何從擴充功能資訊清單第2版（VSIX v2）升級為新的第3版 VSIX 資訊清單格式（VSIX v3）。

## <a name="install-visual-studio-2017-with-required-workloads"></a>使用必要的工作負載安裝 Visual Studio 2017

請確定您的安裝包含下列工作負載：

* .NET 桌面開發
* Visual Studio 擴充功能開發

## <a name="open-vsix-solution-in-visual-studio-2017"></a>在 Visual Studio 2017 中開啟 VSIX 方案

所有 VSIX 專案都需要主要版本單向升級為 Visual Studio 2017。

專案檔（例如 **.csproj*）將會更新：

* MinimumVisualStudioVersion-現在設定為15。0
* OldToolsVersion （如果先前存在）-現在設定為14。0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>更新 VSSDK. BuildTools NuGet 套件

> [!Note]
> 如果您的解決方案未參考 BuildTools NuGet 套件，您可以略過此步驟。

為了以新的 VSIX v3 （第3版）格式建立擴充功能，您的解決方案必須以新的 VSSDK Build 工具建立。 這會與 Visual Studio 2017 一起安裝，但您的 VSIX v2 延伸模組可能會透過 NuGet 保留較舊版本的參考。 若是如此，您將需要手動安裝解決方案的 VSSDK BuildTools NuGet 套件更新。

若要更新 VSSDK. BuildTools 的 NuGet 參考：

* 以滑鼠右鍵按一下方案，然後選擇 [**管理方案的 NuGet 套件**]。
* 流覽至 [**更新**] 索引標籤。
* 選取 **[VSSDK BuildTools （最新版本）**]。
* 按 [**更新**]。

![VSSDK 組建工具](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>對 VSIX 擴充功能資訊清單進行變更

若要確保使用者的 Visual Studio 安裝具有執行延伸模組所需的所有元件，請在擴充功能資訊清單檔中指定所有必要條件元件或封裝。 當使用者嘗試安裝延伸模組時，VSIXInstaller 會檢查是否已安裝所有必要條件。 如果部分遺失，系統會提示使用者在延伸模組安裝程式中安裝遺失的元件。

> [!Note]
> 所有延伸模組至少應將 Visual Studio 核心編輯器元件指定為必要條件。

* 編輯延伸模組資訊清單檔案（通常稱為*extension.vsixmanifest*）。
* 請確定 `InstallationTarget` 包含15.0。
* 新增必要的安裝必要條件（如下列範例所示）。
  * 建議您只指定安裝必要條件的元件識別碼。
  * 如需[識別元件識別碼的指示](#find-component-ids)，請參閱本檔結尾的一節。

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>選項：使用設計工具對 VSIX 擴充功能資訊清單進行變更

您可以使用資訊清單設計工具中的 [新增**必要條件**] 索引標籤來選取必要條件，並為您更新 XML，而不是直接編輯資訊清單 XML。

> [!Note]
> 資訊清單設計工具只會讓您選取安裝在目前 Visual Studio 實例上的元件（而非工作負載或封裝）。 如果您需要為目前未安裝的工作負載、封裝或元件新增必要條件，請直接編輯資訊清單 XML。

* 開啟*extension.vsixmanifest [Design]* file。
* 選取 [**必要條件**] 索引標籤，然後按 [**新增**] 按鈕。

   ![VSIX 資訊清單設計工具](media/vsix-manifest-designer.png)

* [**加入新**的必要條件] 視窗隨即開啟。

   ![新增 vsix 先決條件](media/add-vsix-prerequisite.png)

* 按一下 [**名稱**] 的下拉式清單，然後選取所需的先決條件。
* 如有必要，請更新版本。

   > [!Note]
   > [版本] 欄位會預先填入目前已安裝元件的版本，範圍橫跨最多（但不包括）元件的下一個主要版本。

   ![新增 roslyn 先決條件](media/add-roslyn-prerequisite.png)

* 按下 **[確定]**。

## <a name="update-debug-settings-for-the-project"></a>更新專案的偵錯工具設定

如果您想要在 Visual Studio 的實驗實例中檢查延伸模組，請確定**debug**  >  **start 動作**的專案設定具有 [**啟動外部程式：** ] 值設定為 Visual Studio 2017 安裝的*devenv.exe*檔案。

看起來可能像是： *C:\Program Files （x86） \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![啟動外部程式](media/start-external-program.png)

> [!Note]
> Debug Start 動作通常會儲存在 *.csproj. 使用者*檔案中。 這個檔案通常會包含在 *.gitignore*檔案中，因此，在認可至原始檔控制時，通常不會與其他專案檔一起儲存。 因此，如果您從原始檔控制中提取了您的方案，可能是因為專案沒有設定起始動作的值。 以 Visual Studio 2017 建立的新 VSIX 專案會建立以預設值指向目前 Visual Studio 安裝目錄的 *.csproj. user*檔案。 不過，如果您要遷移 VSIX v2 延伸模組，則 *.csproj. 使用者*檔案可能會包含先前 Visual Studio 版本之安裝目錄的參考。 設定 [ **Debug**Start action] 的值，可在  >  **Start action**您嘗試偵錯工具延伸模組時，讓正確的 Visual Studio 實驗實例啟動。

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>檢查延伸模組是否正確建立（做為 VSIX v3）

* 建立 VSIX 專案。
* 將產生的 VSIX 解壓縮。
  * 根據預設，VSIX 檔案會存留在*bin/Debug*或*bin/Release*中，做為 *[YourCustomExtension] .vsix*。
  * 將 *.vsix*重新命名為 *.zip* ，以輕鬆地查看內容。
* 檢查三個檔案是否存在：
  * *延伸模組。 extension.vsixmanifest*
  * *manifest.js于*
  * *catalog.js于*

## <a name="check-when-all-required-prerequisites-are-installed"></a>檢查是否已安裝所有必要的必要條件

測試 VSIX 是否在已安裝所有必要必要條件的電腦上成功安裝。

> [!Note]
> 在安裝任何延伸模組之前，請關閉 Visual Studio 的所有實例。

嘗試安裝延伸模組：

* 在 Visual Studio 2017

![Visual Studio 2017 上的 VSIX 安裝程式](media/vsixinstaller-vs-2017.png)

* 選擇性：檢查 Visual Studio 的舊版。
  * 證明回溯相容性。
  * 應適用于 Visual Studio 2012、Visual Studio 2013 Visual Studio 2015。
* 選擇性：檢查 VSIX 安裝程式版本檢查是否提供版本選擇。
  * 包含舊版的 Visual Studio （如果已安裝）。
  * 包含 Visual Studio 2017。

如果 Visual Studio 最近開啟，您可能會看到如下的對話方塊：

![vs 正在執行的進程](media/vs-running-processes.png)

等候進程關閉，或手動結束工作。 您可以依照列出的名稱，或以括弧列出的 PID 來尋找處理常式。

> [!Note]
> 當 Visual Studio 的實例正在執行時，這些進程不會自動關閉。 請確定您已關閉電腦上的所有 Visual Studio 實例，包括其他使用者的所有實例，然後繼續重試。

## <a name="check-when-missing-the-required-prerequisites"></a>檢查是否遺漏必要的必要條件

* 嘗試在具有 Visual Studio 2017 的電腦上安裝此擴充功能，但不包含必要條件（上述）中定義的所有元件。
* 檢查安裝是否識別出遺失的元件，並將其列為 VSIXInstaller 中的必要條件。
* 注意：如果需要以擴充功能安裝任何必要條件，就需要提高許可權。

![vsixinstaller 缺少必要元件](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>決定元件

查閱您的相依性時，您會發現一個相依性可以對應到多個元件。 若要判斷您應該將哪些相依性指定為您的必要條件，建議您選擇具有類似擴充功能的元件，也可以考慮您的使用者，以及他們最可能安裝或不想要安裝的元件類型。 我們也建議以必要的必要條件來建立延伸模組，讓您的擴充功能能夠執行，而如果未偵測到某些元件，則會讓它們處於休眠狀態。

為了提供進一步的指引，我們已識別出一些常見的延伸模組類型和其建議的必要條件：

擴充功能類型 | 顯示名稱 | ID
--- | --- | ---
編輯器 | Visual Studio 核心編輯器 | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# 和 Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Managed 桌面工作負載核心 | Microsoft.VisualStudio.Component.ManagedDesktop.Core
偵錯工具 | Just-in-Time 偵錯工具 | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>尋找元件識別碼

依 Visual Studio 產品排序的元件清單位於[2017 工作負載和元件識別碼 Visual Studio](/visualstudio/install/workload-and-component-ids?view=vs-2019)。 請在資訊清單中針對您的必要條件識別碼使用這些元件識別碼。

如果您不確定哪個元件包含特定的二進位檔，請下載[元件 > 的二進位對應試算表](https://aka.ms/vs2017componentid-binaries)。

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Excel 工作表中有四個數據行： [**元件名稱**]、[工作元件 **]、[****版本**] 和 [**二進位/檔案名**]。  您可以使用篩選準則來搜尋及尋找特定元件和二進位檔。

針對您所有的參考，請先判斷哪些是在核心編輯器（VisualStudio. CoreEditor）元件中。  我們至少需要將核心編輯器元件指定為所有延伸模組的必要條件。 對於不在核心編輯器中的參考，請在 [**二進位檔/檔案名稱**] 區段中新增篩選，以尋找具有這些參考之任何子集的元件。

範例：

* 如果您有偵錯工具延伸模組，並知道您的專案具有*VSDebugEng.dll*和*VSDebug.dll*的參考，請按一下 [二進位檔 **/檔案名稱**] 標頭中的 [篩選] 按鈕。  搜尋 "VSDebugEng.dll"，然後選取 *[確定]*。  接著再按一下 [二進位檔/檔案**名稱**] 標頭中的 [篩選] 按鈕，然後搜尋 "VSDebug.dll"。  選取 [**新增目前選取專案**] 核取方塊以篩選，然後選取 **[確定]**。  現在請查看**元件名稱**，尋找與您的擴充功能類型最相關的元件。 在此範例中，您會選擇即時偵錯工具，並將它新增至您的 extension.vsixmanifest。
* 如果您知道您的專案會處理偵錯工具元素，您可以在篩選搜尋方塊中搜尋「偵錯工具」，以查看其名稱中包含偵錯工具的元件。

## <a name="specify-a-visual-studio-2017-release"></a>指定 Visual Studio 2017 版本

如果您的擴充功能需要特定版本的 Visual Studio 2017，例如，它取決於15.3 中發行的功能，您必須在 VSIX **InstallationTarget**中指定組建編號。 例如，版本15.3 的組建編號為 ' 15.0.26730.3 '。 您可以在[這裡](../install/visual-studio-build-numbers-and-release-dates.md)看到版本與組建編號的對應。 使用版本號碼 ' 15.3 ' 將無法正確運作。

如果您的擴充功能需要15.3 或更高版本，您會將**InstallationTarget 版本**聲明為 [15.0.26730.3，16.0）：

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
