---
title: "如何： 往返 for Visual Studio 的擴充功能 |Microsoft 文件"
ms.custom: 
ms.date: 06/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
caps.latest.revision: "1"
author: willbrown
ms.author: willbrown
manager: justinclareburt
ms.workload: willbrown
ms.openlocfilehash: b51673daa7a8c3526ad7de7f7cfdeac6a91d3b4b
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2018
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>如何： 讓擴充功能與 Visual Studio 2017 和 Visual Studio 2015 相容

本文件說明如何讓 Visual Studio 2015 和 Visual Studio 2017 之間反覆存取的擴充性專案。 完成之後此升級，專案將能夠開啟、 建置、 安裝和執行 Visual Studio 2015 和 Visual Studio 2017 中。  做為參考，可以往返 Visual Studio 2015 和 Visual Studio 2017 之間的某些延伸模組都可以找到[這裡](https://github.com/Microsoft/VSSDK-Extensibility-Samples)中 Microsoft 的擴充性範例。

如果您只想要在 Visual Studio 2017，建置，但是想要輸出執行 Visual Studio 2015 和 Visual Studio 2017 的 VSIX，則參考[延伸模組移轉文件](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)。

>**注意：**在 Visual Studio 版本之間的變更，因為工作在其中一個版本的某些作業將無法運作另一個。 確定您嘗試存取的功能都可在這兩個版本中，或擴充功能將會有非預期的結果。

以下是您將會完成，往返 VSIX 本文件中的步驟大綱：

1. 匯入正確的 NuGet 封裝。
2. 更新擴充功能資訊清單：
    * 安裝目標
    * 必要條件
3. 更新 CSProj:
    * 更新`<MinimumVisualStudioVersion>`。
    * 新增`<VsixType>`屬性。
    * 加入偵錯屬性`($DevEnvDir)`3 次。
    * 加入匯入的建置工具和目標條件。

4. 建置和測試

## <a name="environment-setup"></a>環境設定

本文件假設您已經在電腦上安裝下列項目：

* Visual Studio 2015 安裝 VS SDK
* Visual Studio 2017，與安裝的擴充性工作負載

## <a name="recommended-approach"></a>建議的方法

強烈建議使用 Visual Studio 2015，而不是 Visual Studio 2017 啟動這項升級。 在 Visual Studio 2015 中開發的主要優點是確保不會參考不可以使用 Visual Studio 2015 中的組件。 如果您開發的 Visual Studio 2017，會有相依性的組件僅存在於 Visual Studio 2017，可能會造成的風險。

## <a name="ensure-there-is-no-reference-to-projectjson"></a>請確定沒有參考加入 project.json

本文件稍後我們將會插入條件式匯入 *.csproj 檔案中的陳述式。  如果您 NuGet 參考會儲存在 project.json 中，這不會運作。 因此，建議您移動所有 NuGet 參考 packages.config 檔案。
如果您的專案包含 project.json 檔案：

* 記下一個參考在 project.json 中。
* 從 [方案總管] 中，刪除從專案的 project.json 檔案。
    * 這將刪除 project.json 檔案，並將它從專案移除。
* 新增 NuGet 參考加回專案。
    * 以滑鼠右鍵按一下方案，然後選擇 **管理方案的 NuGet 套件...**
    * Visual Studio 會自動為您建立 packages.config 檔案

>**注意：**如果您的專案包含 EnvDTE 封裝，他們可能需要加上按一下滑鼠右鍵**參考**選取**將參考加入**並加入適當的參考。  使用 NuGet 封裝，可能會嘗試建置專案時建立的錯誤。

## <a name="adding-appropriate-build-tools"></a>新增適當的建置工具

我們需要先加入可讓我們來建置和偵錯適當的建置工具。 Microsoft 已建立此呼叫 Microsoft.VisualStudio.Sdk.BuildTasks 的組件。

若要建置並部署在 Visual Studio 2015 和 2017年 VSIXv3，您將需要下列 NuGet 套件：

版本 | 建置的工具
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

若要這樣做：

* 將 NuGet 套件 Microsoft.VisualStudio.Sdk.BuildTasks.14.0 加入至您的專案。
* 如果您的專案不包含 Microsoft.VSSDK.BuildTools，請將它加入。
* 請確認 Microsoft.VSSDK.BuildTools 版本 15.x 或更高。

## <a name="update-extension-manifest"></a>更新擴充功能資訊清單

### <a name="1-installation-targets"></a>1.安裝目標

我們要告知 Visual Studio 版本為目標來建立 VSIX。  一般而言，這些參考是版本 14.0 (Visual Studio 2015)，或是版本 15.0 (Visual Studio 2017)。  在此案例中，我們想要建立將用於兩者，安裝擴充功能，所以我們需要兩個版本為目標的 VSIX。  如果您想要建置和安裝在版本早於 14.0 您 VSIX，即可啟用此設定的較早的版本號碼;不過，不再支援 10.0 或更早版本。

* 在 Visual Studio 中，開啟 source.extension.vsixmanifest 檔案。
* 開啟**安裝目標** 索引標籤。
* 變更**版本範圍**至 [14.0，16.0）。  ' [' 會告知包括超過它的 14.0 和所有版本的 Visual Studio。  ')' 會告知 Visual Studio，以包含，但不是包括版本 16.0 15.0 的所有版本。
* 儲存所有變更並關閉所有 Visual Studio 執行個體。

![安裝目標映像](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2.加入 extension.vsixmanifest 檔案的必要條件

必要條件是 Visual Studio 2017 的新功能。  在此情況下，我們需要 Visual Studio 核心編輯器做為必要條件。 因為 Visual Studio 2015 VSIX 設計工具不會處理新`Prerequisites` 區段中，您必須編輯的 XML 程式碼中手動這個組件。  或者，您可以開啟 Visual Studio 2017，然後使用更新的資訊清單設計工具插入的必要條件。

若要手動執行此作業：

* 瀏覽至 [檔案總管] 中的專案目錄。
* 開啟`extension.vsixmanifest`使用文字編輯器的檔案。
* 加入下列標記：

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* 儲存並關閉檔案。

>**注意：**如果您選擇要完成這項作業與在 Visual Studio 2017 VSIX 設計工具，您必須手動編輯必要的版本以確認它是所有版本的 Visual Studio 2017 相容。  這是因為設計工具會為您目前版本的 Visual Studio (例如，15.0.26208.0) 插入的最小版本。  不過，因為其他使用者可能會有較早版本，您會想要手動編輯這個檔案來 15.0。

此時，您的資訊清單檔案看起來應該像下面這樣：

![必要條件範例](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>修改專案檔 (myproject.csproj)

強烈建議具有已修改的.csproj 開啟時執行這個步驟的參考。  您可以找到數個範例[這裡](https://github.com/Microsoft/VSSDK-Extensibility-Samples)。  選取任何擴充性範例、 尋找.csproj 檔案，以供參考，然後執行下列步驟：

* 瀏覽至 [檔案總管] 中的專案目錄。
* 使用文字編輯器開啟 myproject.csproj 檔案。

### <a name="1-update-the-minimumvisualstudioversion"></a>1.更新 MinimumVisualStudioVersion

* 若要設定的最小的 visual studio 版本`$(VisualStudioVersion)`並將新增的條件陳述式。  如果它們尚不存在，請新增這些標籤。  請確定標記已設定，如下所示：

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2.加入 VsixType 屬性

* 加入下列標記`<VsixType>v3</VsixType>`至屬性群組。

>**注意：**建議加入下面`<OutputType></OutputType>`標記。

### <a name="3-add-the-debugging-properties"></a>3.加入偵錯屬性

* 加入下列的屬性群組：

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* 從.csproj 檔和任何刪除以下的所有執行個體。 副檔名為.csproj.user 檔案：

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4.將條件加入至建置工具匯入

* 加入額外的條件陳述式來`<import>`Microsoft.VSSDK.BuildTools 參考的標記。  只要插入`'$(VisualStudioVersion)' != '14.0' And`在條件陳述式的前面。  這些陳述式會出現在頁首和頁尾的 csproj 檔案中。

例如: 

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* 加入額外的條件陳述式來`<import>`Microsoft.VisualStudio.Sdk.BuildTasks.14.0 的標記。  只要插入`'$(VisualStudioVersion)' == '14.0' And`在條件陳述式的前面。 這些陳述式會出現在頁首和頁尾的 csproj 檔案中。

例如: 

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* 加入額外的條件陳述式來`<Error>`Microsoft.VSSDK.BuildTools 參考的標記。  只要插入`'$(VisualStudioVersion)' != '14.0' And`在條件陳述式的前面。 這些陳述式會出現在頁尾的 csproj 檔案中。

例如: 

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* 加入額外的條件陳述式來`<Error>`Microsoft.VisualStudio.Sdk.BuildTasks.14.0 的標記。  只要插入`'$(VisualStudioVersion)' == '14.0' And`在條件陳述式的前面。 這些陳述式會出現在頁尾的 csproj 檔案中。

例如: 

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* 儲存於 csproj 檔案並關閉它。

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Visual Studio 2015 和 Visual Studio 2017 測試擴充功能安裝

此時，您的專案應該準備好要建置可以安裝於 Visual Studio 2015 和 Visual Studio 2017 VSIXv3。

* Visual Studio 2015 中開啟您的專案
* 建置您的專案，並確認 VSIX 建置正確的輸出
* 瀏覽至您的專案目錄
* 開啟筒]-> [偵錯資料夾
* 按兩下 VSIX 檔案，並在 Visual Studio 2015 和 Visual Studio 2017 安裝您的擴充功能
* 請確定您可以看到工具擴充功能]-> [擴充功能和更新的 「 安裝 」 一節。
* 嘗試執行/使用的延伸模組來檢查它的運作

![尋找在 VSIX](media/finding-a-VSIX-example.png)

>**注意：**如果訊息 」 開啟檔案"強制關閉 Visual Studio 停止您的專案，瀏覽至您的專案目錄，顯示隱藏的資料夾，並刪除.vs 資料夾。
