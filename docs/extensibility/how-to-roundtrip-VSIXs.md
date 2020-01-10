---
title: 如何往返擴充功能
ms.date: 06/25/2017
ms.topic: conceptual
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: madsk
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 44b5c5c58c46017730f06142548505c628894a11
ms.sourcegitcommit: b04c603ce73b993d042ebdf7f3722cf4fe2ef7f4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74316493"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>如何：讓擴充功能與 Visual Studio 2017 和 Visual Studio 2015 相容

本檔說明如何在 Visual Studio 2015 和 Visual Studio 2017 之間進行擴充性專案的往返。 完成此升級之後，專案將能夠在 Visual Studio 2015 和 Visual Studio 2017 中開啟、建立、安裝及執行。 如需參考，您可以在[VS SDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples)擴充性範例中找到一些可以在 Visual Studio 2015 和 Visual Studio 2017 之間來回往返的延伸模組。

如果您只想要在 Visual Studio 2017 中建立，但希望輸出 VSIX 同時在 Visual Studio 2015 和 Visual Studio 2017 中執行，則請參閱[延伸模組遷移檔](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)。

> [!NOTE]
> 由於版本之間 Visual Studio 的變更，因此在某個版本中運作的某些專案不會在另一個版本中執行。 請確認您嘗試存取的功能在這兩個版本中都可使用，否則延伸模組將會產生非預期的結果。

以下是您將在本檔中完成的步驟概述，以反復存取 VSIX：

1. 匯入正確的 NuGet 套件。
2. 更新延伸模組資訊清單：
    * 安裝目標
    * 必要條件
3. 更新 .Csproj：
    * 更新 `<MinimumVisualStudioVersion>`。
    * 新增 `<VsixType>` 屬性。
    * 將 [調試] 屬性加入 `($DevEnvDir)` 3 次。
    * 新增匯入組建工具和目標的條件。

4. 組建和測試

## <a name="environment-setup"></a>環境設定

本檔假設您已在電腦上安裝下列各項：

* 已安裝 VS SDK 的 Visual Studio 2015
* 已安裝擴充性工作負載的 Visual Studio 2017

## <a name="recommended-approach"></a>建議的方法

強烈建議使用 Visual Studio 2015 來啟動此升級，而不是 Visual Studio 2017。 在 Visual Studio 2015 中進行開發的主要優點，是為了確保您不會參考 Visual Studio 2015 中未提供的元件。 如果您在 Visual Studio 2017 中進行開發，則可能會對只存在於 Visual Studio 2017 中的元件引入相依性。

## <a name="ensure-there-is-no-reference-to-projectjson"></a>請確定沒有對專案的參考。 json

稍後在本檔中，我們會在您的 * *.csproj*檔案中插入條件式匯入語句。 如果您的 NuGet 參考儲存在*專案 json*中，這將無法正常執行。 因此，建議您將所有 NuGet 參考移至*封裝 .config*檔案。
如果您的專案包含*專案 json*檔案：

* 記下*專案. json*中的參考。
* 從**方案總管**，刪除專案中的*專案. json*檔案。 這會刪除*專案. json*檔案，並將它從專案中移除。
* 將 NuGet 參考重新加入至專案：
  * 以滑鼠右鍵按一下**方案**，然後選擇 [**管理方案的 NuGet 套件**]。
  * Visual Studio 會自動為您建立*封裝 .config*檔案。

> [!NOTE]
> 如果您的專案包含 EnvDTE 套件，您可能需要以滑鼠右鍵按一下 [**參考**]，然後選取 [新增**參考**] 並新增適當的參考來新增它們。 使用 NuGet 套件時，可能會在嘗試建立您的專案時產生錯誤。

## <a name="add-appropriate-build-tools"></a>新增適當的組建工具

我們必須確定新增組建工具，讓我們能夠適當地建立和進行偵錯工具。 Microsoft 已建立這個名為 VisualStudio 的元件。 BuildTasks。

若要在 Visual Studio 2015 和2017中建立及部署 VSIXv3，您將需要下列 NuGet 套件：

版本 | 建立的工具
--- | ---
Visual Studio 2015 | VisualStudio. BuildTasks 14。0
Visual Studio 2017 | VSSDK. BuildTool

方法如下：

* 將 VisualStudio NuGet 套件新增至您的專案。
* 如果您的專案不包含 VSSDK. BuildTools，請將它加入。
* 請確定 VSSDK. BuildTools 版本為 15. x 或更高。

## <a name="update-extension-manifest"></a>更新延伸模組資訊清單

### <a name="1-installation-targets"></a>1. 安裝目標

我們需要告訴 Visual Studio 要以何種版本做為建立 VSIX 的目標。 這些參考通常是14.0 版（Visual Studio 2015）、15.0 版（Visual Studio 2017）或版本16.0 （Visual Studio 2019）。 在我們的案例中，我們想要建立一個 VSIX 來安裝兩者的延伸模組，因此我們需要以這兩個版本為目標。 如果您想要在14.0 之前的版本上建立和安裝 VSIX，可以藉由設定舊版號碼來完成此作業。不過，已不再支援10.0 版和更早版本。

* 在 Visual Studio 中，開啟*extension.vsixmanifest*檔案。
* 開啟 [**安裝目標**] 索引標籤。
* 將**版本範圍**變更為 [14.0，17.0）。 ' [' 會告訴 Visual Studio 包含14.0 和所有過去的版本。 '） ' 會告知 Visual Studio 包含17.0 版以上的所有版本，但不包括在內。
* 儲存所有變更，並關閉 Visual Studio 的所有實例。

![安裝目標映射](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. 將必要條件新增至*extension.vsixmanifest*檔案

我們需要 Visual Studio 核心編輯器做為必要條件。 開啟 Visual Studio，並使用更新的資訊清單設計工具來插入必要條件。

若要手動執行此動作：

* 流覽至 [檔案瀏覽器] 中的專案目錄。
* 使用文字編輯器開啟*extension.vsixmanifest*檔案。
* 新增下列標記：

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* 儲存並關閉檔案。

> [!NOTE]
> 您可能需要手動編輯先決條件版本，以確保它與所有版本的 Visual Studio 2017 相容。 這是因為設計工具會將最小版本插入 Visual Studio 您目前的版本（例如，15.0.26208.0）。 不過，由於其他使用者可能會有較舊的版本，因此您會想要手動將此編輯為15.0。

此時，您的資訊清單檔看起來應該像這樣：

![必要條件範例](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>修改專案檔（myproject .csproj）

強烈建議您在執行此步驟時，參考已修改的 .csproj 開啟。 您可以在[這裡](https://github.com/Microsoft/VSSDK-Extensibility-Samples)找到幾個範例。 選取任何擴充性範例，尋找 *.csproj*檔案以供參考，然後執行下列步驟：

* 流覽至 [檔案**瀏覽器**] 中的專案目錄。
* 使用文字編輯器開啟*myproject*檔案。

### <a name="1-update-the-minimumvisualstudioversion"></a>1. 更新 MinimumVisualStudioVersion

* 將最小的 visual studio 版本設定為 `$(VisualStudioVersion)`，並為其新增條件陳述式。 新增這些標記（如果不存在）。 請確定標記設定如下：

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. 加入 VsixType 屬性。

* 將下列標記 `<VsixType>v3</VsixType>` 新增至屬性群組。

> [!NOTE]
> 建議您將此新增至 `<OutputType></OutputType>` 標籤下方。

### <a name="3-add-the-debugging-properties"></a>3. 加入調試屬性

* 新增下列屬性群組：

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartProgram>$(DevEnvDir)devenv.exe</StartProgram>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* 從 *.csproj*檔案和任何 *.csproj. user*檔案中，刪除下列程式碼範例的所有實例：

```xml
<StartAction>Program</StartAction>
<StartProgram>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartProgram>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. 將條件新增至組建工具匯入

* 將額外的條件陳述式加入至 VSSDK BuildTools 參考的 `<import>` 標記。 在條件陳述式的前方插入 `'$(VisualStudioVersion)' != '14.0' And`。 這些語句會出現在 .csproj 檔案的頁首和頁尾中。

例如：

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* 將其他條件陳述式加入至具有 VisualStudio 的 `<import>` 標記中。 在條件陳述式的前方插入 `'$(VisualStudioVersion)' == '14.0' And`。 這些語句會出現在 .csproj 檔案的頁首和頁尾中。

例如：

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* 將額外的條件陳述式加入至 VSSDK BuildTools 參考的 `<Error>` 標記。 若要這麼做，請在條件陳述式的前方插入 `'$(VisualStudioVersion)' != '14.0' And`。 這些語句會出現在 .csproj 檔案的頁尾中。

例如：

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* 將其他條件陳述式加入至具有 VisualStudio 的 `<Error>` 標記中。 在條件陳述式的前方插入 `'$(VisualStudioVersion)' == '14.0' And`。 這些語句會出現在 .csproj 檔案的頁尾中。

例如：

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* 儲存 .csproj 檔案並加以關閉。

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>在 Visual Studio 2015 和 Visual Studio 2017 中測試延伸模組安裝

此時，您的專案應該已準備好建立可在 Visual Studio 2015 和 Visual Studio 2017 上安裝的 VSIXv3。

* 在 Visual Studio 2015 中開啟您的專案。
* 建立您的專案，並在輸出中確認 VSIX 已正確建立。
* 流覽至您的專案目錄。
* 開啟 [ *\bin\Debug* ] 資料夾。
* 按兩下 VSIX 檔案，並在 Visual Studio 2015 和 Visual Studio 2017 上安裝您的擴充功能。
* 請確定您可以在 [**已安裝**] 區段中的 [**工具**] > [**延伸模組和更新**] 中看到延伸模組。
* 嘗試執行/使用延伸模組來檢查其是否正常運作。

![尋找 VSIX](media/finding-a-VSIX-example.png)

> [!NOTE]
> 如果您的專案在**開啟**檔案的訊息停止回應，請強制關閉 Visual Studio、流覽至您的專案目錄、顯示隱藏的資料夾，然後刪除*vs*資料夾。
 