---
title: 如何往返延伸模組
description: 瞭解如何在 Visual Studio 2015 與 Visual Studio 2019 或 Visual Studio 2017 之間進行 Visual Studio 擴充性專案來回行程。
ms.custom: SEO-VS-2020
ms.date: 06/25/2017
ms.topic: how-to
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: madsk
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 3db3264bf5226b5679452659928e451e7975b001
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993610"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-20192017-and-visual-studio-2015"></a>How to：使擴充功能與 Visual Studio 2019/2017 和 Visual Studio 2015 相容

本檔說明如何在 Visual Studio 2015 與 Visual Studio 2019 或 Visual Studio 2017 之間進行擴充性專案的往返。 完成這項升級之後，專案將能夠以 Visual Studio 2015 和 Visual Studio 2019 或2017來開啟、建立、安裝及執行。 您可以在 [VS SDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples)擴充性範例中，找到可在 Visual Studio 2015 和 Visual Studio 2019 或2017之間進行往返的一些延伸模組參考。

如果您只想要在 Visual Studio 2019/2017 中建立，但希望輸出 VSIX 在 Visual Studio 2015 和 Visual Studio 2019/2017 中執行，則請參閱擴充功能 [遷移檔](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)。

> [!NOTE]
> 因為版本之間的 Visual Studio 有所變更，所以在某個版本中運作的某些專案無法在另一個版本中運作。 確定您嘗試存取的功能可在這兩個版本中使用，否則延伸模組將會產生非預期的結果。

以下是您將在此檔中完成的步驟大綱，以進行 VSIX 的往返：

1. 匯入正確的 NuGet 套件。
2. 更新擴充功能資訊清單：
    * 安裝目標
    * 必要條件
3. 更新 .Csproj：
    * 更新 `<MinimumVisualStudioVersion>`。
    * 新增 `<VsixType>` 屬性。
    * 加入調試屬性 `($DevEnvDir)` 3 次。
    * 新增匯入組建工具和目標的條件。

4. 組建與測試

## <a name="environment-setup"></a>環境設定

本檔假設您已在電腦上安裝下列各項：

* 已安裝 VS SDK 的 Visual Studio 2015
* 已安裝擴充工作負載的 Visual Studio 2019 或2017

## <a name="recommended-approach"></a>建議的方法

強烈建議您使用 Visual Studio 2015 來開始這項升級，而不是 Visual Studio 2019 或2017。 在 Visual Studio 2015 中開發的主要優點，是確保您不會參考 Visual Studio 2015 中未提供的元件。 如果您在 Visual Studio 2019 或2017中進行開發，則可能會產生相依于只存在於 Visual Studio 2019 或2017之元件的相依性。

## <a name="ensure-there-is-no-reference-to-projectjson"></a>確定沒有 project.js的參考

稍後在本檔中，我們將在您的 **.csproj* 檔案中插入條件式匯入語句。 如果您的 NuGet 參考儲存在 *project.js* 中，這將無法運作。 因此，建議您將所有 NuGet 參考移至 *packages.config* 檔案。
如果您的專案包含檔案 *上的project.js* ：

* 記下 *project.js* 的參考。
* 從 **方案總管** 中，刪除專案中的 *project.js* 檔案。 這會刪除檔案 *上的project.js* ，並將它從專案中移除。
* 將 NuGet 參考新增回專案：
  * 以滑鼠右鍵按一下 **方案** ，然後選擇 [ **管理方案的 NuGet 套件**]。
  * Visual Studio 會自動為您建立 *packages.config* 檔。

> [!NOTE]
> 如果您的專案包含 EnvDTE 封裝，可能需要以滑鼠右鍵按一下 [**加入參考**]，然後加入適當 **的參考，** 以加入這些封裝。 使用 NuGet 套件可能會在嘗試建立專案時產生錯誤。

## <a name="add-appropriate-build-tools"></a>新增適當的組建工具

我們需要務必加入 build tools，讓我們能夠適當地建立和偵錯工具。 Microsoft 已建立名為 VisualStudio 的元件，稱為 BuildTasks。

若要在 Visual Studio 2015 和2019/2017 中建立和部署 VSIXv3，您需要下列 NuGet 套件：

版本 | 建立的工具
--- | ---
Visual Studio 2015 | VisualStudio. BuildTasks 14。0
Visual Studio 2019 或2017 | VSSDK. BuildTool

操作方法：

* 將 NuGet 套件 VisualStudio 新增至您的專案。
* 如果您的專案不包含 VSSDK. BuildTools，請將它加入。
* 請確定 VSSDK BuildTools 版本是 15. x 或更高版本。

## <a name="update-extension-manifest"></a>更新擴充功能資訊清單

### <a name="1-installation-targets"></a>1. 安裝目標

我們需要告訴 Visual Studio 要建立 VSIX 的目標版本。 這些參考通常是 14.0 (Visual Studio 2015) 、版本 15.0 (Visual Studio 2017) 或版本 16.0 (Visual Studio 2019) 。 在我們的案例中，我們想要建立一個可為兩者安裝擴充功能的 VSIX，因此我們必須以這兩個版本為目標。 如果您希望 VSIX 在14.0 之前的版本上建立並安裝，可透過設定舊版號碼來完成此操作;不過，不再支援10.0 版和更舊版本。

* 在 Visual Studio 中開啟 *extension.vsixmanifest* 檔案。
* 開啟 [ **安裝目標** ] 索引標籤。
* 將 **版本範圍** 變更為 [14.0，17.0) ]。 ' [' 會告知 Visual Studio 包含14.0 和所有過去的版本。 「) 」會告知 Visual Studio 包含最多（但不包括）17.0 版的所有版本。
* 儲存所有變更並關閉 Visual Studio 的所有實例。

![安裝目標映射](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. 將必要條件新增至 *extension.vsixmanifest* 檔案

我們需要 Visual Studio 核心編輯器作為必要條件。 開啟 Visual Studio，並使用更新的資訊清單設計工具插入必要條件。

若要手動執行此動作：

* 流覽至檔案總管中的專案目錄。
* 使用文字編輯器開啟 *extension.vsixmanifest* 檔案。
* 新增下列標記：

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* 儲存並關閉檔案。

> [!NOTE]
> 您可能需要手動編輯必要條件版本，以確保其與所有版本的 Visual Studio 2019 或2017相容。 這是因為設計工具會插入最小版本做為您目前版本的 Visual Studio (例如 15.0.26208.0) 。 不過，因為其他使用者可能會有較舊的版本，所以您會想要手動將其編輯為15.0。

此時，您的資訊清單檔案看起來應該像這樣：

![必要條件範例](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>修改專案檔 (myproject .csproj) 

強烈建議您在執行此步驟時，參考已修改的 .csproj 開啟。 您可以在 [這裡](https://github.com/Microsoft/VSSDK-Extensibility-Samples)找到數個範例。 選取任何擴充性範例、尋找 *.csproj* 檔案以供參考，然後執行下列步驟：

* 流覽至 **檔案總管** 中的專案目錄。
* 使用文字編輯器開啟 *myproject .csproj* 檔案。

### <a name="1-update-the-minimumvisualstudioversion"></a>1. 更新 MinimumVisualStudioVersion

* 將 visual studio 的最小版本設定為 `$(VisualStudioVersion)` ，並為其新增條件陳述式。 如果這些標記不存在，請新增這些標記。 請確定標記的設定如下：

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. 新增 VsixType 屬性。

* 將下列標記加入 `<VsixType>v3</VsixType>` 至屬性群組。

> [!NOTE]
> 建議您將它新增至標記下方 `<OutputType></OutputType>` 。

### <a name="3-add-the-debugging-properties"></a>3. 加入調試屬性

* 新增下列屬性群組：

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartProgram>$(DevEnvDir)devenv.exe</StartProgram>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* 從 *.csproj* 檔案和任何 *.csproj. 使用者* 檔案中，刪除下列程式碼範例的所有實例：

```xml
<StartAction>Program</StartAction>
<StartProgram>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartProgram>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. 將條件新增至組建工具匯入

* 將其他條件陳述式新增至 `<import>` 具有 VSSDK. BuildTools 參考的標記。 `'$(VisualStudioVersion)' != '14.0' And`在條件陳述式的前方插入。 這些語句會出現在 .csproj 檔案的頁首和頁尾中。

例如：

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* 將額外的條件陳述式新增至 `<import>` 具有 VisualStudio 的標記。 `'$(VisualStudioVersion)' == '14.0' And`在條件陳述式的前方插入。 這些語句會出現在 .csproj 檔案的頁首和頁尾中。

例如：

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* 將其他條件陳述式新增至 `<Error>` 具有 VSSDK. BuildTools 參考的標記。 若要這麼做，請 `'$(VisualStudioVersion)' != '14.0' And` 在 condition 語句的前面插入。 這些語句會出現在 .csproj 檔案的頁尾。

例如：

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* 將額外的條件陳述式新增至 `<Error>` 具有 VisualStudio 的標記。 `'$(VisualStudioVersion)' == '14.0' And`在條件陳述式的前方插入。 這些語句會出現在 .csproj 檔案的頁尾。

例如：

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* 儲存 .csproj 檔案並加以關閉。 
  * 請注意，如果您在方案中使用一個以上的專案，請使用專案操作功能表上的 [設定為啟始專案]，將此專案設定為啟始專案) 。 這可確保在您卸載此專案之後，Visual Studio 重新開啟此專案。

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2019-or-2017"></a>測試擴充功能安裝 Visual Studio 2015 和 Visual Studio 2019 或2017

此時，您的專案應該已準備好建立可同時安裝在 Visual Studio 2015 和 Visual Studio 2017 上的 VSIXv3。

* 在 Visual Studio 2015 中開啟您的專案。
* 建立您的專案，並在輸出中確認 VSIX 建立正確。
* 流覽至您的專案目錄。
* 開啟 *\bin\Debug* 資料夾。
* 按兩下 VSIX 檔案，然後在 Visual Studio 2015 和 Visual Studio 2019/2017 上安裝您的擴充功能。
* 請確定您可以在  >  [**已安裝**] 區段的 [工具 **擴充功能和更新**] 中看到延伸模組。
* 嘗試執行/使用延伸模組以檢查它是否正常運作。

![尋找 VSIX](media/finding-a-VSIX-example.png)

> [!NOTE]
> 如果您的專案停止回應 **開啟** 檔案的訊息，請強制關閉 Visual Studio、流覽至您的專案目錄、顯示隱藏的資料夾，以及刪除 *vs* 資料夾。
