---
title: 如何往返擴充功能
ms.date: 06/25/2017
ms.topic: conceptual
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: gregvanl
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 809ca83d164b4cb589f19438b1fc5672cc1b4b8e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880948"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>HOW TO：讓擴充功能與 Visual Studio 2017 和 Visual Studio 2015 相容

本文件說明如何讓 Visual Studio 2015 和 Visual Studio 2017 之間反覆存取的擴充性專案。 完成這項升級之後, 的專案就可以開啟、 建置、 安裝及 Visual Studio 2015 和 Visual Studio 2017 中執行。 做為參考，可以反覆存取 Visual Studio 2015 和 Visual Studio 2017 之間的某些延伸模組可在[VS SDK 擴充性範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)。

如果您只想要建置在 Visual Studio 2017，但想要輸出至 Visual Studio 2015 和 Visual Studio 2017 中執行的 VSIX，然後指向[延伸模組移轉文件](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)。

> [!NOTE]
> 由於在 Visual Studio 版本之間的變更，在另一個中無法運作之前在其中一個版本的一些事項。 請確定您嘗試存取的功能可用於這兩個版本，或擴充功能會有非預期的結果。

以下是您將會完成這份文件，若要反覆存取的 VSIX 中的步驟概述：

1. 匯入正確的 NuGet 套件。
2. 更新擴充功能資訊清單：
    * 安裝目標
    * 必要條件
3. 更新 CSProj:
    * 更新`<MinimumVisualStudioVersion>`。
    * 新增`<VsixType>`屬性。
    * 新增偵錯屬性`($DevEnvDir)`3 次。
    * 加入匯入組建工具和目標的條件。

4. 建置和測試

## <a name="environment-setup"></a>環境設定

本文件假設您已在電腦上安裝下列項目：

* Visual Studio 2015 安裝 VS SDK
* 已安裝的擴充性工作負載的 visual Studio 2017

## <a name="recommended-approach"></a>建議的方法

它是強烈建議使用 Visual Studio 2015，而不是 Visual Studio 2017 啟動這項升級。 在 Visual Studio 2015 中開發的主要優點是，以確保不會參考不可以使用 Visual Studio 2015 中的組件。 如果您執行 Visual Studio 2017 中的開發時，會有您可能會造成相依於組件只存在於 Visual Studio 2017 的風險。

## <a name="ensure-there-is-no-reference-to-projectjson"></a>請確定沒有任何以 project.json 參考

在本文中，稍後我們會插入條件式匯入陳述式中的您 **.csproj*檔案。  如果您的 NuGet 參考會儲存在這將無法運作*project.json*。 因此，建議您移動所有 NuGet 參考*packages.config*檔案。
如果您的專案包含*project.json*檔案：

* 請記下的在參考*project.json*。
* 從**方案總管**，刪除*project.json*從專案的檔案。 這會刪除*project.json*檔案，並將它從專案移除。
* 新增 NuGet 參考回至專案：
    * 以滑鼠右鍵按一下**解決方案**，然後選擇**管理方案的 NuGet 套件**。
    * Visual Studio 會自動建立*packages.config*為您的檔案。

> [!NOTE]
> 如果您的專案包含 EnvDTE 套件，它們可能需要以滑鼠右鍵按一下要加入**參考**選取**將參考加入**並新增適當的參考。  使用 NuGet 套件，可能會嘗試建置專案時建立的錯誤。

## <a name="add-appropriate-build-tools"></a>新增適當的建置工具

我們必須確定將建置工具，讓我們建置和偵錯適當。 Microsoft 已建立此呼叫 Microsoft.VisualStudio.Sdk.BuildTasks 的組件。

若要建置並部署在 Visual Studio 2015 和 2017年 VSIXv3，您將需要下列 NuGet 封裝：

版本 | 建置的工具
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

方法如下：

* 新增 NuGet 套件 Microsoft.VisualStudio.Sdk.BuildTasks.14.0 至您的專案。
* 如果您的專案不包含 Microsoft.VSSDK.BuildTools，請將它新增。
* 請確定 Microsoft.VSSDK.BuildTools 版本 15.x 或更新版本。

## <a name="update-extension-manifest"></a>更新擴充功能資訊清單

### <a name="1-installation-targets"></a>1.安裝目標

我們要告訴 Visual Studio 版本為目標來建置 VSIX。  一般而言，這些參考會為 14.0 (Visual Studio 2015) 的版本或版本 15.0 (Visual Studio 2017)。  在我們的案例中，我們想要建置會針對兩者安裝延伸模組，因此我們需要以這兩個版本為目標的 VSIX。  若要讓您建置和 14.0 比更早版本上安裝的 VSIX，做法是藉由設定較早的版本號碼;不過，不再支援 10.0 及更早版本。

* 開啟*source.extension.vsixmanifest* Visual Studio 中的檔案。
* 開啟**安裝目標** 索引標籤。
* 變更**版本範圍**到 [14.0，16.0）。  ' [' 會告知 Visual Studio 包括 14.0 和所有的版本，過去它。  ')' 會告知要包含的 15.0，但不是包含版本 16.0 的所有版本的 Visual Studio。
* 儲存所有變更並關閉所有 Visual Studio 執行個體。

![安裝目標映像](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2.加入必要條件*extension.vsixmanifest*檔案

必要條件是使用 Visual Studio 2017 的新功能。  在此案例中，我們需要 Visual Studio 核心編輯器做為必要條件。 因為 Visual Studio 2015 VSIX 設計工具不會處理新`Prerequisites` 區段中，您必須編輯此組件中的 XML 程式碼以手動方式。  或者，您可以開啟 Visual Studio 2017，並使用更新的資訊清單設計工具插入的必要條件。

若要以手動方式這樣：

* 瀏覽至 [檔案總管] 中的專案目錄。
* 開啟*extension.vsixmanifest*使用文字編輯器的檔案。
* 新增下列標記：

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* 儲存並關閉檔案。

> [!NOTE]
> 如果您選擇達成此目的使用 VSIX 設計工具，Visual Studio 2017 中，您必須手動編輯必要的版本，以確保它是與所有版本的 Visual Studio 2017 相容。  這是因為設計工具會為您目前版本的 Visual Studio (比方說，15.0.26208.0) 插入的最小版本。  不過，因為其他使用者可能會有較早版本，您會想要以手動方式編輯這個檔案為 15.0。

此時，您的資訊清單檔應看起來像這樣：

![必要條件範例](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>修改專案檔 (myproject.csproj)

強烈建議將修改後的.csproj 開啟時執行此步驟的參考。  您可以找到數個範例[此處](https://github.com/Microsoft/VSSDK-Extensibility-Samples)。  選取任何擴充性範例中，尋找 *.csproj*檔案的參考，然後執行下列步驟：

* 瀏覽至專案目錄中**檔案總管**。
* 開啟*myproject.csproj*使用文字編輯器的檔案。

### <a name="1-update-the-minimumvisualstudioversion"></a>1.更新 MinimumVisualStudioVersion

* 若要設定的最小的 visual studio 版本`$(VisualStudioVersion)`，並將它加入的條件陳述式。  如果它們尚不存在，請新增這些標記。  確定設定標記，如下所示：

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2.新增 VsixType 屬性。

* 新增下列標記`<VsixType>v3</VsixType>`至屬性群組。

> [!NOTE]
> 建議將此新增下面`<OutputType></OutputType>`標記。

### <a name="3-add-the-debugging-properties"></a>3.新增偵錯屬性

* 加入下列屬性群組：

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* 刪除下列程式碼範例中的所有執行個體 *.csproj*檔案和任何 *.csproj.user*檔案：

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4.將條件加入至組建工具匯入

* 加入額外的條件式陳述式來`<import>`Microsoft.VSSDK.BuildTools 參考的標記。  插入`'$(VisualStudioVersion)' != '14.0' And`條件陳述式前面。  這些陳述式會出現在頁首和頁尾的 csproj 檔案。

例如: 

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* 加入額外的條件式陳述式來`<import>`Microsoft.VisualStudio.Sdk.BuildTasks.14.0 的標記。 插入`'$(VisualStudioVersion)' == '14.0' And`條件陳述式前面。 這些陳述式會出現在頁首和頁尾的 csproj 檔案。

例如: 

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* 加入額外的條件式陳述式來`<Error>`Microsoft.VSSDK.BuildTools 參考的標記。  執行這項操作，藉由插入`'$(VisualStudioVersion)' != '14.0' And`條件陳述式前面。 這些陳述式會出現在頁尾中的 csproj 檔案。

例如: 

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* 加入額外的條件式陳述式來`<Error>`Microsoft.VisualStudio.Sdk.BuildTasks.14.0 的標記。  插入`'$(VisualStudioVersion)' == '14.0' And`條件陳述式前面。 這些陳述式會出現在頁尾中的 csproj 檔案。

例如: 

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* 儲存 csproj 檔案，並將它關閉。

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>在 Visual Studio 2015 和 Visual Studio 2017 測試擴充功能安裝

此時，您的專案應該已準備好建置可以在 Visual Studio 2015 和 Visual Studio 2017 安裝 VSIXv3。

* Visual Studio 2015 中開啟您的專案。
* 建置您的專案，並確認在 VSIX 建置正確的輸出。
* 瀏覽至您的專案目錄。
* 開啟 *\bin\Debug* 資料夾。
* 按兩下 VSIX 檔案，並在 Visual Studio 2015 和 Visual Studio 2017 中安裝擴充功能。
* 請確定您可以看到中的擴充功能**工具** > **擴充功能和更新**中**已安裝**一節。
* 嘗試執行/使用的延伸模組來檢查它的運作。

![尋找在 VSIX](media/finding-a-VSIX-example.png)

> [!NOTE]
> 如果您的專案時停止回應與訊息**開啟檔案**、 強制關閉 Visual Studio 中，瀏覽至您的專案目錄，顯示隱藏的資料夾，和刪除 *.vs*資料夾。