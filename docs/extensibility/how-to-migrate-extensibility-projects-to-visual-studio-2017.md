---
title: 如何： 將擴充性專案移轉至 Visual Studio 2017 |Microsoft 文件
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 93f5d663a31d43dc7a52cbd11261ca78134c682a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133525"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>如何： 將擴充性專案移轉至 Visual Studio 2017

本文件說明如何將擴充性專案升級至 Visual Studio 2017。 除了說明如何更新專案檔，它也會說明如何從延伸模組資訊清單版本 2 (VSIX v2) 升級至新第 3 版 VSIX 資訊清單的格式 (VSIX v3)。

## <a name="install-visual-studio-2017-with-required-workloads"></a>安裝 Visual Studio 2017 必要的工作負載

請確定您的安裝包含下列工作負載：

* .NET 桌面開發
* Visual Studio 擴充功能開發

## <a name="open-vsix-solution-in-visual-studio-2017"></a>在 Visual Studio 2017 中開啟的 VSIX 方案

所有的 VSIX 專案將需要 Visual Studio 2017 主要版本單向升級。

將更新專案檔 (例如 *.csproj):

* MinimumVisualStudioVersion-現在設定為 15.0
* OldToolsVersion (如果先前存在)-現在設定為 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>更新 Microsoft.VSSDK.BuildTools NuGet 套件

>**注意：** 如果您的方案未參考 Microsoft.VSSDK.BuildTools NuGet 封裝，您可以略過此步驟。

若要建置您的延伸模組中新的 VSIX v3 （第 3 版） 格式，您的方案將需要使用新的 VSSDK 建置工具來建置。 這將會隨 Visual Studio 2017，但您的 VSIX v2 擴充功能可能會緊透過 NuGet 較舊版本的參考。 如果是這樣，您必須手動安裝更新為您的方案 Microsoft.VSSDK.BuildTools NuGet 套件。

若要更新 Microsoft.VSSDK.BuildTools NuGet 參考：

* 以滑鼠右鍵按一下方案，然後選擇 **管理方案的 NuGet 套件...**
* 瀏覽至**更新** 索引標籤。
* 選取 Microsoft.VSSDK.BuildTools （最新版本）。
* 按**更新**。

![VSSDK 建置工具](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>變更 VSIX 擴充功能資訊清單

若要確保使用者的 Visual Studio 安裝程式已執行此擴充功能所需的所有組件，指定延伸模組資訊清單檔案中的所有必要條件元件或封裝。 當使用者嘗試安裝此擴充功能時，VSIXInstaller 會檢查如果已安裝所有必要條件。 如果某些遺漏時，就會提示使用者安裝遺漏的元件擴充功能的安裝程序的一部分。

>**注意：** 最少，所有擴充功能應該指定 Visual Studio 核心編輯器元件為必要條件。

* 編輯擴充功能資訊清單檔案 （通常稱為 source.extension.vsixmanifest）。
* 請確定`InstallationTarget`包含 15.0。
* （如下列範例所示），請加入必要的安裝必要條件。
  * 我們建議您指定只安裝的必要條件元件識別碼。
  * 請參閱此文件結尾區段[指示識別元件識別碼](#finding-component-ids)。

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>選項： 使用設計工具來進行 VSIX 擴充功能資訊清單中的變更

而不是直接編輯資訊清單 XML，您可以使用新**必要條件** 索引標籤中選取必要條件的資訊清單設計工具和 XML 將會為您更新。

>**注意：** 資訊清單設計工具只會允許您選取目前的 Visual Studio 執行個體所安裝的元件 （沒有工作負載或封裝）。 如果您要新增為工作負載、 封裝或目前未安裝的元件的必要元件，請直接編輯 XML 資訊清單。

* 開啟 [設計] source.extension.vsixmanifest 檔案。
* 選取**必要條件** 索引標籤，然後按**新增** 按鈕。

  ![VSIX 資訊清單設計工具](media/vsix-manifest-designer.png)

* **新增新必要條件**視窗隨即開啟。

  ![加入 vsix 必要條件](media/add-vsix-prerequisite.png)

* 上的下拉式清單按一下**名稱**及選取所需的必要條件。
* 視需要更新的版本。

  >注意: [版本] 欄位會預先填入目前已安裝的元件，與範圍最多跨越 （但不是包括） 的版本元件的下一個主要版本。

  ![新增 roslyn 必要條件](media/add-roslyn-prerequisite.png)

* Press **OK**.

## <a name="update-debug-settings-for-project"></a>更新專案的偵錯設定

如果您想要偵錯您的 Visual Studio 的實驗執行個體中的擴充功能，請確定專案設定**偵錯** > **起始動作**具有**啟動外部程式：** 值設定為您的 Visual Studio 2017 安裝 devenv.exe 檔。

它看起來可能像是：

```
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe
```

![啟動外部程式](media/start-external-program.png)

>**注意：** 偵錯起始動作通常儲存在。 副檔名為.csproj.user 檔案。 這個檔案通常會納入到.gitignore 檔案並，因此，不通常會儲存其他專案時使用檔案認可至原始檔控制。 因此，如果您有提取您的方案從原始檔控制全新很可能將必須為啟動動作設定任何值的專案。 使用 Visual Studio 2017 建立新的 VSIX 專案都有。 以指向目前的 Visual Studio 安裝目錄的預設值建立的副檔名為.csproj.user 檔案。 不過如果您正在移轉 v2 VSIX 擴充功能，則可能的。 副檔名為.csproj.user 檔案會包含先前 Visual Studio 版本的安裝目錄的參考。 設定的值**偵錯** > **起始動作**將允許正確 Visual Studio 實驗執行個體啟動時您嘗試偵錯您的擴充功能。

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>請檢查擴充功能建置正確 （如 VSIX v3)

* 建立 VSIX 專案。
* 將解壓縮產生的 VSIX。
  * 藉由預設值，VSIX 檔案生活 bin/Debug 內 或者 [YourCustomExtension].vsix 為的 bin/Release。
  * 將.vsix 重新命名為.zip，以輕鬆地檢視內容。
* 檢查有三個檔案存在：
  * extension.vsixmanifest
  * manifest.json
  * catalog.json

## <a name="check-when-all-required-prerequisites-are-installed"></a>當已安裝所有必要的先決條件檢查

此 VSIX 仍會成功安裝在電腦安裝所有必要的先決條件的測試。

>**注意：** 之前安裝任何擴充功能，請關閉所有 Visual Studio 執行個體。

嘗試安裝此擴充功能：

* 在 Visual Studio 2017

![在 Visual Studio 2017 VSIX 安裝程式](media/vsixinstaller-vs-2017.png)

* 選擇性： 檢查有舊版 Visual Studio。
  * 證明回溯相容性。
  * 應該適用於 Visual Studio 2012、 Visual Studio 2013、 Visual Studio 2015。
* 選擇性： 檢查 VSIX 安裝程式版本檢查提供選擇的版本。
  * 包含了舊版的 Visual Studio （如果安裝的話）。
  * 包含 Visual Studio 2017。

如果最近開啟 Visual Studio，您可能會看到對話方塊，像這樣：

![vs 執行處理程序](media/vs-running-processes.png)

等候處理程序，才能關閉，或以手動方式結束工作。 您可以找到處理程序所列的名稱，或使用括號中列出的 PID。

>**注意：** 這些處理程序將不會自動關閉 Visual Studio 的執行個體正在執行時。 請確認您在機器-包括其他使用者，從 Visual Studio 的所有執行個體已關閉，然後繼續重試。

## <a name="check-when-missing-the-required-prerequisites"></a>核取時遺漏所需的必要條件

* 嘗試延伸模組的電腦上安裝 Visual Studio 2017 並不會包含與必要條件 （請見上方） 中定義的所有元件。
* 請檢查安裝識別遺漏的元件/s 和列為 VSIXInstaller 中的先決條件。
* 注意： 提高權限將會需要如果任何必要條件需要安裝擴充功能。

![vsixinstaller 遺失的先決條件](media/vsixinstaller-missing-prerequisite.png)

## <a name="deciding-on-components"></a>決定元件

當查閱程式相依性，您會發現一種相依性會對應到多個元件。 若要判斷哪些相依性，您應該指定為您的必要條件，我們建議您選擇的功能類似於您的擴充功能的元件，以及同時考慮您的使用者和何種類型的元件則最有可能安裝或不介意安裝。 我們也建議您的擴充功能所需的必要條件，滿足可讓您執行的擴充功能的最小的方式和其他功能，讓它們是休眠如果某些元件不會偵測到的建置。

若要進一步提供指引，我們已識別幾個常見的擴充功能類型和其建議的必要條件：

擴充功能類型 | 顯示名稱 | ID
--- | --- | ---
編輯器 | Visual Studio 核心編輯器  | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# 和 Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Managed 桌面工作負載核心 | Microsoft.VisualStudio.Component.ManagedDesktop.Core
偵錯工具 | Just-in-Time 偵錯工具 | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="finding-component-ids"></a>尋找元件識別碼

依照 Visual Studio 產品的元件清單位於[Visual Studio 2017 工作負載與元件識別碼](https://aka.ms/vs2017componentIDs)。 您必要條件的 Id，在您的資訊清單中使用這些元件的識別碼。

如果您不確定哪一個元件包含特定的二進位檔，下載[元件]-> [二進位對應試算表](https://aka.ms/vs2017componentid-binaries)。

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

在 Excel 工作表中有四個資料行：**元件名稱**， **ComponentId**，**版本**，和**二進位 / 檔案名稱**。  您可以使用篩選來搜尋並找出特定的元件和二進位檔。

針對您所有的參考，請先判斷哪些是核心編輯器 (Microsoft.VisualStudio.Component.CoreEditor) 元件中。  最小值，我們需要指定為所有擴充功能的必要元件的核心編輯器元件。 參考剩餘的核心編輯器中，加入篩選條件中的**二進位碼檔案 / 檔案名稱**區段，以尋找具有任何這些參考子集的元件。

例如：

* 如果您有偵錯工具擴充功能，並了解您的專案有 VSDebugEng.dll 和 VSDebug.dll 的參考，按一下篩選按鈕中**二進位碼檔案 / 檔案名稱**標頭。  搜尋"VSDebugEng.dll 」，並選取 [確定]。  接下來按一下 [篩選] 按鈕，在**二進位碼檔案 / 檔案名稱**一次標頭，並搜尋"VSDebug.dll"。  選取核取方塊 」 新增目前的選取範圍來篩選 」，選取 [確定]。  現在看起來**元件名稱**了大部分的元件相關的延伸類型。 在此範例中，您會選擇的時間只需偵錯工具，並將它加入至您 vsixmanifest。
* 如果您知道您的專案處理與偵錯工具項目，您可以搜尋 「 偵錯工具 」 篩選器的 [搜尋] 方塊中查看哪些元件包含其名稱中偵錯工具上。

## <a name="specifying-a-visual-studio-2017-release"></a>指定 Visual Studio 2017 版本

如果您的擴充功能需要特定版本的 Visual Studio 2017，比方說，這取決於 15.3 發行一項功能，您必須指定組建編號，在您的 VSIX 中**InstallationTarget**。 例如，版本 15.3 有 '15.0.26730.3' 組建編號。 您可以看到的組建編號的版本對應[這裡](../install/visual-studio-build-numbers-and-release-dates.md)。 使用 版次號碼 '15.3' 將無法正常運作。

如果您的擴充功能需要 15.3 或更高版本，您就可以宣告**InstallationTarget 版本**為 [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```