---
title: 作法：將擴充性專案移轉至 Visual Studio 2017 |Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 802c55844be14192ea5bd5de1870e27e2063ccad
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319316"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>HOW TO：將擴充性專案移轉至 Visual Studio 2017

本文件說明如何將擴充性專案升級至 Visual Studio 2017。 除了說明如何更新專案檔，它也會說明如何從延伸模組資訊清單版本 2 (VSIX v2) 升級至新第 3 版 VSIX 資訊清單的格式 (VSIX v3)。

## <a name="install-visual-studio-2017-with-required-workloads"></a>安裝必要的工作負載的 Visual Studio 2017

請確定您的安裝包含下列工作負載：

* .NET 桌面開發
* Visual Studio 擴充功能開發

## <a name="open-vsix-solution-in-visual-studio-2017"></a>在 Visual Studio 2017 中開啟 VSIX 方案

所有的 VSIX 專案將會需要的主要版本的單向升級至 Visual Studio 2017。

專案檔 (例如 * *.csproj*) 將會更新：

* MinimumVisualStudioVersion-現在設定為 15.0
* OldToolsVersion (如果先前存在)-現在設定為 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>更新 Microsoft.VSSDK.BuildTools NuGet 套件

> [!Note]
> 如果您的解決方案未參考 Microsoft.VSSDK.BuildTools NuGet 套件，您可以略過此步驟。

若要建置您新的 VSIX v3 中的擴充功能 （第 3 版） 格式，您的解決方案將需要使用新的 VSSDK 建置工具來建置。 這將會安裝 Visual Studio 2017 中，但您的 VSIX v2 延伸模組可能會保留較舊的版本，透過 NuGet 的參考。 如果是這樣，您必須手動安裝您的解決方案 Microsoft.VSSDK.BuildTools NuGet 套件的更新。

若要更新 Microsoft.VSSDK.BuildTools NuGet 參考：

* 以滑鼠右鍵按一下方案，然後選擇 **管理方案的 NuGet 套件**。
* 瀏覽至**更新** 索引標籤。
* 選取  **Microsoft.VSSDK.BuildTools （最新版）** 。
* 按下**更新**。

![VSSDK 建置工具](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>對 VSIX 延伸模組資訊清單中的變更

若要確保使用者的 Visual Studio 安裝有執行擴充功能所需的所有組件，請指定所有必要的元件或套件延伸模組資訊清單檔案中。 當使用者嘗試安裝擴充功能時，VSIXInstaller 會檢查是否已安裝所有必要條件。 如果某些遺漏時，就會提示使用者安裝遺漏的元件延伸模組的安裝程序的一部分。

> [!Note]
> 最小值，所有延伸模組應該指定 Visual Studio 核心編輯器元件為必要條件。

* 編輯擴充功能資訊清單檔 (通常稱為*source.extension.vsixmanifest*)。
* 請確定`InstallationTarget`包含 15.0。
* （如下列範例所示），請加入必要的安裝必要條件。
   * 我們建議您指定只安裝必要條件的元件識別碼。
   * 請參閱本文件的最後一節[識別元件識別碼的指示](#find-component-ids)。

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>選項：使用設計工具對 VSIX 延伸模組資訊清單中的變更

而不是直接編輯資訊清單 XML，您可以使用新**必要條件**選取必要條件的資訊清單設計工具 和 XML 索引標籤將會更新為您。

> [!Note]
> 資訊清單設計工具將只允許您選取目前的 Visual Studio 執行個體所安裝的元件 （沒有工作負載或封裝）。 如果您需要將工作負載、 封裝或目前未安裝的元件的必要條件，請直接編輯資訊清單 XML。

* 開啟*source.extension.vsixmanifest [設計]* 檔案。
* 選取 [**必要條件**索引標籤，然後按**新增**] 按鈕。

   ![VSIX 資訊清單設計工具](media/vsix-manifest-designer.png)

* **新增新必要條件**視窗隨即開啟。

   ![新增 vsix 必要條件](media/add-vsix-prerequisite.png)

* 下拉式清單中按一下**名稱**，然後選取所需的必要條件。
* 如有必要，請更新的版本。

   > [!Note]
   > [版本] 欄位會預先填入目前已安裝的元件，與範圍最多可跨越 （但不是包括） 的版本元件的下一個主要版本。

   ![新增 roslyn 必要條件](media/add-roslyn-prerequisite.png)

* 按 [確定]  。

## <a name="update-debug-settings-for-the-project"></a>更新專案的偵錯設定

如果您想要偵錯您的 Visual Studio 的實驗執行個體的延伸模組，請確定專案設定，如**偵錯** > **起始動作**具有**啟動外部程式：** 值設定為*devenv.exe* Visual Studio 2017 安裝的檔案。

它可能如下：*C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![啟動外部程式](media/start-external-program.png)

> [!Note]
> 偵錯起始動作通常會儲存於 *.csproj.user*檔案。 這個檔案通常包含在 *.gitignore*檔案，並因此，不通常會儲存與認可至原始檔控制時的其他專案檔案。 因此，如果您已預先採用了您的解決方案從原始檔控制全新很可能專案會有任何啟動動作設定的值。 使用 Visual Studio 2017 中建立新的 VSIX 專案會有 *.csproj.user*以指向目前的 Visual Studio 安裝目錄的預設值建立的檔案。 不過如果您要移轉 v2 VSIX 擴充功能，它可能是所 *.csproj.user*檔案會包含先前的 Visual Studio 版本的安裝目錄的參考。 設定的值**偵錯** > **起始動作**可正確 Visual Studio 實驗執行個體啟動時您嘗試偵錯您的延伸模組。

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>請檢查延伸模組建置正確 （如 VSIX v3)

* 建立 VSIX 專案。
* 將解壓縮產生的 VSIX。
   * 根據預設，VSIX 檔案內的所在*bin/Debug*或是*bin/Release*作為 *[YourCustomExtension].vsix*。
   * 重新命名 *.vsix*要 *.zip*來輕鬆地檢視內容。
* 檢查有三個檔案：
   * *extension.vsixmanifest*
   * *manifest.json*
   * *catalog.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>當已安裝所有必要的必要條件檢查

VSIX 成功安裝在電腦安裝所有必要先決條件的測試。

> [!Note]
> 在安裝之前任何延伸模組，請關閉所有 Visual Studio 執行個體。

嘗試安裝擴充功能：

* 在 Visual Studio 2017

![在 Visual Studio 2017 的 VSIX 安裝程式](media/vsixinstaller-vs-2017.png)

* 選擇項：請檢查先前的 Visual Studio 版本。
   * 證明回溯相容性。
   * 應該適用於 Visual Studio 2012、 Visual Studio 2013，Visual Studio 2015。
* 選擇項：VSIX 安裝程式版本檢查程式，提供各種版本檢查。
   * （如果已安裝），包括舊版的 Visual Studio。
   * 包含 Visual Studio 2017。

如果最近開啟 Visual Studio，您可能會看到如下的對話方塊：

![與執行中處理序](media/vs-running-processes.png)

等候處理序關閉，或以手動方式結束工作。 所列的名稱，或 pid 為以括號，您可以找到處理程序。

> [!Note]
> 這些程序將不會自動關閉 Visual Studio 執行個體正在執行時。 請確認您已關閉的機器-包括其他使用者，在 Visual Studio 的所有執行個體，然後繼續重試。

## <a name="check-when-missing-the-required-prerequisites"></a>核取時遺漏所需的必要條件

* 嘗試安裝擴充功能的電腦上使用 Visual Studio 2017 並不會包含的必要條件 （請見上方） 中定義的所有元件。
* 安裝識別遺漏的元件/秒，並列為 VSIXInstaller 在必要條件檢查。
* 注意:如果需要安裝擴充功能的任何必要條件，將會需要提高權限。

![vsixinstaller 遺漏的必要條件](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>決定元件

當查閱您的相依性，您會發現一個相依性會對應到多個元件。 若要判斷哪些相依性，您應該指定為您的必要條件，我們建議您選擇的元件，類似於您的延伸模組的功能，並同時考慮您的使用者和元件的何種他們最有可能已安裝或不會記住此安裝。 我們也建議您以所需的必要條件，滿足可讓您擴充功能執行的最小的方式和其他功能的擴充功能有休眠，如果有特定元件不會偵測到他們的建置。

若要提供進一步的指引，我們已找出幾個常見的擴充功能類型和其建議的必要條件：

延伸模組類型 | 顯示名稱 | 識別碼
--- | --- | ---
編輯器 | Visual Studio 核心編輯器 | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# 和 Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Managed 桌面工作負載核心 | Microsoft.VisualStudio.Component.ManagedDesktop.Core
偵錯工具 | Just-in-Time 偵錯工具 | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>元件識別碼

依 Visual Studio 產品排序的元件清單位於[Visual Studio 2017 工作負載和元件識別碼](https://aka.ms/vs2017componentIDs)。 使用您必要條件的識別碼，在您的資訊清單中的這些元件的識別碼。

如果您不確定哪些元件包含特定的二進位檔，請下載[元件]-> [二進位對應試算表](https://aka.ms/vs2017componentid-binaries)。

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

在 Excel 工作表中有四個資料行：**元件名稱**， **ComponentId**，**版本**，和**二進位檔名 /** 。  您可以使用篩選來搜尋及尋找特定元件和二進位檔。

針對您所有的參考，請先判斷哪些是在核心編輯器 (Microsoft.VisualStudio.Component.CoreEditor) 元件。  最小值，我們會要求必須指定為所有擴充功能的必要元件的核心編輯器元件。 參考會保留不在核心編輯器中，將篩選條件中的加入**二進位檔 / 檔案名稱**一節，以尋找具有任何這些參考子集的元件。

例如：

* 如果您有偵錯工具擴充功能，並了解您的專案有參考*VSDebugEng.dll*並*VSDebug.dll*，按一下 [篩選] 按鈕，在**二進位檔 / 檔名**標頭。  搜尋"VSDebugEng.dll 」 並選取*確定*。  接下來按一下 [篩選] 按鈕，在**二進位檔 / 檔案名稱**一次標頭，並搜尋 「 VSDebug.dll"。  選取此核取方塊**加入目前的選取範圍來篩選**，然後選取**確定**。  現在瀏覽**元件名稱**找到大部分的元件與擴充功能類型。 在此範例中，您會選擇的時間只需偵錯工具，並將它加入您 vsixmanifest。
* 如果您知道您的專案會處理與偵錯工具項目，您可以搜尋 「 偵錯工具 」 在篩選搜尋方塊中查看哪些元件包含其名稱中的偵錯工具。

## <a name="specify-a-visual-studio-2017-release"></a>指定 Visual Studio 2017 版本

如果您的延伸模組需要特定版本的 Visual Studio 2017，比方說，這取決於在 15.3 中發行的功能，您必須在您的 VSIX 中指定的組建編號**InstallationTarget**。 例如，版本 15.3 會有 '15.0.26730.3' 組建編號。 您所見的對應版本的組建編號[此處](../install/visual-studio-build-numbers-and-release-dates.md)。 使用版本號碼 '15.3' 將無法正常運作。

如果您的延伸模組需要 15.3 或更新版本中，您會宣告**InstallationTarget 版本**為 [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
