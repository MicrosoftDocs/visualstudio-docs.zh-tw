---
title: 更新 Visual Studio 延伸模組
description: 瞭解如何更新您的 Visual Studio 延伸模組，以使用 Visual Studio 2022。
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 6e7c4990d513bfb276984611b2d38f3e35a825eb
ms.sourcegitcommit: a7a4c5545a269ca74a7291966ff77afb3b57f5ce
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2021
ms.locfileid: "112424649"
---
# <a name="update-a-visual-studio-extension-for-visual-studio-2022"></a>更新 Visual Studio 2022 的 Visual Studio 延伸模組

> [!IMPORTANT]
> 本指南的建議旨在引導開發人員遷移擴充功能，這些擴充功能需要主要變更才能在 Visual Studio 2019 和2022中運作。 在這些情況下，建議使用兩個 VSIX 專案和條件式編譯。
> 許多延伸模組都能在 Visual Studio 2019 和2022中運作，而且不需要遵循本指南中現代化延伸模組的建議。
> 在 Visual Studio 2022 中試用您的延伸模組，並評估您的延伸模組最適合的選項。

您可以遵循本指南來更新您的延伸模組，以使用 Visual Studio 2022 Preview。 Visual Studio 2022 Preview 是64位應用程式，並引進了 VS SDK 的一些重大變更。 本指南將逐步引導您完成使用目前的 Visual Studio 2022 預覽版來使用您的延伸模組所需的步驟，讓您的擴充功能可在 Visual Studio 2022 達到 GA 之前，供使用者安裝。

## <a name="installing"></a>安裝

從 [Visual Studio 2022 preview 下載](https://visualstudio.microsoft.com/vs/preview/vs2022)安裝 Visual Studio 2022 preview。

### <a name="extensions-written-in-a-net-language"></a>以 .NET 語言撰寫的延伸模組

適用于受控擴充的 Visual Studio 2022 的 VS SDK *以專用* 于 NuGet：

- VisualStudio) 中繼套件的[](https://www.nuget.org/packages/Microsoft.VisualStudio.Sdk/) (2.x 版會帶入您需要的大部分或所有參考元件。
- 您應從 VSIX 專案參考 [VSSDK. BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools/) (2.x 版本) 套件，讓它能夠建立符合2022規範的 Visual Studio vsix。

延伸模組 *必須* 使用「任何 CPU」或「x64」平臺進行編譯。 "X86" 平臺與 Visual Studio 2022 的64位進程不相容。

### <a name="extensions-written-in-c"></a>以 c + + 撰寫的延伸模組

使用 c + + 編譯之延伸模組的 VS SDK，與往常一樣，已安裝的 Visual Studio SDK 可供使用。

擴充功能 *必須* 專門針對 VISUAL STUDIO 2022 SDK 和 amd64 進行編譯。

### <a name="update-your-extension-to-visual-studio-2022"></a>將您的延伸模組更新為 Visual Studio 2022

#### <a name="extensions-with-running-code"></a>執行程式碼的延伸模組

具有執行中程式碼的延伸模組 *必須* 專門針對 Visual Studio 2022 進行編譯。 Visual Studio 2022 將不會載入任何未特別以 Visual Studio 2022 為目標的延伸模組。

瞭解如何將您的預先 Visual Studio 2022 擴充功能遷移至 Visual Studio 2022：

1. [現代化您的專案](#modernize-your-vsix-project)。
1. 將[您的原始程式碼重構到共用專案中](#use-shared-projects-for-multi-targeting)，以允許以 Visual Studio 2022 和較舊版本為目標。
1. [新增 Visual Studio 2022 目標的 VSIX 專案](#add-a-visual-studio-2022-target)，以及我們的 [封裝/元件](migrated-assemblies.md)重新對應表。
1. [進行必要的程式碼調整](#handle-breaking-api-changes)。
1. [測試您的 Visual Studio 2022 延伸](#test-your-extension)模組。
1. [發行您的 Visual Studio 2022 延伸](#publish-your-extension)模組。

#### <a name="extensions-without-running-code"></a>不執行程式碼的延伸模組

未包含任何正在執行之程式碼的延伸模組 (例如，專案/專案範本) *不* 需要遵循上述步驟，包括兩個不同 VSIXs 的生產環境。

相反地，應該修改一個 VSIX，讓它的檔案宣告 `source.extension.vsixmanifest` 兩個安裝目標，如下所示：

```xml
<Installation>
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0,17.0)">
      <ProductArchitecture>x86</ProductArchitecture>
   </InstallationTarget>
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
</Installation>
```

您可以略過本文中有關使用共用專案和多個 VSIXs 的步驟。 您可以繼續進行 [測試](#test-your-extension)！

> [!NOTE]
> 如果您要撰寫 *新* 的 Visual Studio 延伸模組、使用 Visual Studio 2022 預覽版，而且想要 () 目標 Visual Studio 2019 或更早版本，請參閱 [本指南](target-previous-versions.md)。

### <a name="msbuild-tasks"></a>MSBuild 工作

如果您撰寫 MSBuild 工作，請注意，在 Visual Studio 2022 中，更有可能會將它們載入64位 MSBuild.exe 進程。 如果您的工作需要執行32位的進程，請參閱 [此 msbuild 檔](../../msbuild/how-to-configure-targets-and-tasks.md#usingtask-attributes-and-task-parameters) ，以確保 msbuild 知道要在32位進程中載入您的工作。

## <a name="modernize-your-vsix-project"></a>將您的 VSIX 專案現代化

將 Visual Studio 2022 支援新增至您的延伸模組之前，強烈建議您在繼續進行之前，先清除現有專案並將其現代化，包括：

1. [從 packages.config 遷移至 `PackageReference` ](/nuget/consume-packages/migrate-packages-config-to-package-reference)。

1. 將任何直接元件與 SDK 元件參考取代為 PackageReference 專案。

   ```diff
   -<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   +<PackageReference Include="Microsoft.VisualStudio.OLE.Interop" Version="..." />
   ```

   > [!TIP]
   > 您可以只將 *一個* PackageReference *的元件參考* 取代為中繼套件：
   >
   >```diff
   >-<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop.8.0" />
   >+<PackageReference Include="Microsoft.VisualStudio.Sdk" >Version="..." />
   >```

   請務必挑選符合您目標 Visual Studio 最小版本的套件版本。

   某些對 VS SDK 而言不是唯一的元件 (例如，Newtonsoft.Json.dll) 可能已在 Visual Studio 2022 之前透過簡單參考來進行探索， `<Reference Include="Newtonsoft.Json" />` 但 Visual Studio 2022 需要套件參考，因為在 Visual Studio 2022 中，我們會從 MSBuild 的預設元件搜尋路徑移除一些 Visual Studio 執行時間和 SDK 目錄。

   從直接元件參考切換至 NuGet 套件參考，您可能會因為 NuGet 自動安裝相依性的可轉移關閉，而收取其他的元件參考和分析器套件。 這通常是正常的，但可能會導致在您的組建期間標示額外的警告。 完成這些警告並盡可能解決問題，並考慮隱藏無法使用程式碼區域來解決的警告 `#pragma warning disable <id>` 。

## <a name="use-shared-projects-for-multi-targeting"></a>針對多目標使用共用專案

[共用專案](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) 是在 Visual Studio 2015 中引進的專案類型。 Visual Studio 中的共用專案可讓您在多個專案之間共用原始程式碼檔案，並使用條件式編譯符號和唯一的參考集來建立不同的組建。

因為 Visual Studio 2022 需要來自所有先前 VS 版本的一組不同的參考元件，所以我們的指導方針是使用共用的專案，方便您將擴充功能設定為預先 Visual Studio 2022，並 Visual Studio 2022 (和更新) 版本，以提供程式碼共用，但不同的參考。

在 Visual Studio 擴充功能的環境中，您可能會有一個適用于 Visual Studio 2022 和更新版本的 VSIX 專案，以及一個適用于 Visual Studio 2019 和更早版本的 VSIX 專案。 這些專案中的每一個都只會包含一個和一個套件參考，也就是對 `source.extension.vsixmanifest` 16. x sdk 或 17. x sdk 的參考。 這些 VSIX 專案也會有新共用專案的共用專案參考，此專案會裝載您所有可在兩個 VS 版本間共用的原始程式碼。

作為起點，我們會假設您已經有一個以 Visual Studio 2019 為目標的 VSIX 專案，而且您想要在 Visual Studio 2022 上使用您的擴充功能。

您可以使用 Visual Studio 2019 來完成這些步驟。

1. 如果您尚未這麼做，請將 [您的專案現代化](#modernize-your-vsix-project) ，以簡化此更新程式中的後續步驟。

1. 針對每個參考 VS SDK 的現有專案，將新的共用專案加入至方案。
   ![新增專案命令 ](media/update-visual-studio-extension/add-new-project.png)
    ![ 新增專案範本](media/update-visual-studio-extension/new-shared-project-template.png)

1. 將每個 VS SDK 參考專案的參考新增至其共用專案對應專案。
   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="新增共用的專案參考" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. 將所有的 (原始程式碼（包括 .cs、.resx) 從每個 VS SDK 參考的專案）移至其共用專案對應專案。
將檔案保留 `source.extension.vsixmanifest` 在 VSIX 專案中。
   ![共用專案包含所有原始檔](media/update-visual-studio-extension/source-files-in-shared-project.png)

1. 中繼資料檔案 (版本資訊、授權、圖示等) 和 .VSCT 檔案應該移至共用目錄，並新增為 VSIX 專案的連結檔案。
   ![新增中繼資料和 .VSCT 檔作為連結的檔案](media/update-visual-studio-extension/add-linked-items-to-vsix.png)
    - 若為中繼資料檔案，請將 BuildAction 設定為， `Content` 並將 Include 納入 VSIX 中 `true` 。

      ![在 VSIX 中包含中繼資料檔案](./media/update-visual-studio-extension/include-metadata-files-in-vsix.png)
    - 若為 .VSCT 檔，請將 BuildAction 設定為， `VSCTCompile` 而不要包含在 VSIX 中。
      Visual Studio 可能會抱怨這項設定不受支援，但您可以藉由卸載專案並變更為，手動變更組建動作 `Content``VSCTCompile`

    ```diff
    -<Content Include="..\SharedFiles\VSIXProject1Package.vsct">
    -  <Link>VSIXProject1Package.vsct</Link>
    -</Content>
    +<VSCTCompile Include="..\SharedFiles\VSIXProject1Package.vsct">
    +  <Link>VSIXProject1Package.vsct</Link>
    +  <ResourceName>Menus.ctmenu</ResourceName>
    +</VSCTCompile>
    ```

      ![將 .VSCT 檔案設定為 VSCTCompile](media/update-visual-studio-extension/build-linked-vsct-files.png)

1. ) 建立您的專案 (，以確認您未引進任何新的錯誤。

您的專案現在已準備好新增 Visual Studio 2022 支援。

## <a name="add-a-visual-studio-2022-target"></a>新增 Visual Studio 2022 目標

本檔假設您已完成將 [Visual Studio 擴充功能納入共用專案](#use-shared-projects-for-multi-targeting)的步驟。

使用下列步驟，繼續將 Visual Studio 2022 支援新增至您的延伸模組，這些步驟可能會使用 Visual Studio 2019 完成：

1. 將新的 VSIX 專案加入至方案。 這會是以 Visual Studio 2022 為目標的專案。 移除範本隨附的任何原始程式碼，但 *保留該 `source.extension.vsixmanifest`* 檔案。

1. 在新的 VSIX 專案上，將共用的專案參考加入至您 Visual Studio 2019-以 VSIX 參考為目標的相同共用專案。

   ![具有一個共用專案和兩個 VSIX 專案的方案](media/update-visual-studio-extension/shared-project-with-two-heads.png)

1. 確認新的 VSIX 專案已正確建立。 您可能需要加入參考以符合原始 VSIX 專案，以解決任何編譯器錯誤。

1. 針對受管理的 VS 延伸模組，請使用 NuGet 封裝管理員或直接編輯專案檔，將您的套件參考從 16. x (或較舊的) 更新為 Visual Studio 2022 目標專案檔中的 17. x 套件版本：

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    ```

   您將使用從 nuget.org 實際提供的版本。先前使用的專案僅供示範之用。

   在許多情況下，套件識別碼已變更。 請參閱 [套件/元件對應表](migrated-assemblies.md) ，以取得 Visual Studio 2022 中的變更清單。

   以 c + + 撰寫的擴充功能還沒有可供編譯的可用 SDK。

1. 若是 c + + 專案，則必須針對 amd64 進行編譯。 針對受控擴充功能，請考慮將您的專案從為任何 CPU 的組建變更為目標 `x64` ，以反映在 Visual Studio 2022 中，您的延伸模組一律會在64位進程中載入。 `Any CPU` 也沒問題，但如果您參考任何 x64 專用的二進位檔，可能會產生警告。

   您的擴充功能在原生模組上可能具有的任何相依性，都必須從 x86 映射更新為 amd64 映射。

1. 編輯您的檔案 `source.extension.vsixmanifest` ，以反映 Visual Studio 2022 的目標。 設定 `<InstallationTarget>` 標記以反映 Visual Studio 2022，並指出 amd64 承載：

   ```xml
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
   ```

   在 Visual Studio 2019 中，這個檔案的設計工具不會公開新的 `ProductArchitecture` 元素，因此必須使用 xml 編輯器來完成這項變更，您可以使用 **方案總管** 中的 [**開啟** 檔案] 命令來存取。

   這 `ProductArchitecture` 是關鍵元素。 Visual Studio 2022 *不* 會安裝您的延伸模組。

   | 元素 | 值 | 描述 |
   | - | - | - |
   | ProductArchitecture | X86、AMD64 | 此 VSIX 支援的平臺。 不區分大小寫。 每個元素一個平臺，每個 InstallTarget 一個元素。 針對小於17.0 的產品版本，預設值為 x86，可以省略。  如果是產品版本17.0 和更新版本，則需要此元素，而且沒有預設值。 針對 Visual Studio 2022，此元素唯一有效的內容為 "amd64"。 |

1. 在您的 extension.vsixmanifest 中，進行任何其他需要的調整，以符合以 Visual Studio 2019 (的) 。 在資訊清單的元素中，VSIX 的識別碼在 `Identity` 這兩個延伸模組中都是相同的。

此時，您會有 Visual Studio 2022 目標的延伸模組 VSIX。 您應建立您的 Visual Studio 2022 目標 VSIX 專案，並 [完成任何出現的組建中斷](#handle-breaking-api-changes)。 如果您的 Visual Studio 2022 目標 VSIX 專案中沒有組建中斷，恭喜：您已準備好進行測試！

## <a name="handle-breaking-api-changes"></a>處理中斷的 API 變更

Visual Studio 2022 中有 [中斷的 API 變更](breaking-api-list.md) ，可能需要您的程式碼在舊版本上執行時才會變更。 請參閱該檔，以取得如何為每個更新您的程式碼的秘訣。

調整您的程式碼時，建議您使用 [條件式編譯](#use-conditional-compilation-symbols) ，讓您的程式碼可以繼續支援預先 Visual Studio 的2022，同時新增對 Visual Studio 2022 的支援。

當您取得 Visual Studio 2022 目標的延伸模組建立時，請繼續進行 [測試](#test-your-extension)。

## <a name="use-conditional-compilation-symbols"></a>使用條件式編譯符號

如果您想要使用相同的原始程式碼（甚至是相同的檔案）來 Visual Studio 2022 和較早的版本，您可能需要使用條件式編譯，讓您可以派生程式碼以適應中斷性變更。 條件式編譯是 c #、Visual Basic 和 c + + 語言的一項功能，可用來共用大部分的程式碼，同時在特定位置容納分歧的 Api。

若要瞭解如何使用預處理器指示詞和條件式編譯符號的詳細資訊，請參閱 Microsoft 檔 [#if 預處理器](/dotnet/csharp/language-reference/preprocessor-directives#conditional-compilation)指示詞。

以較早 Visual Studio 版本為目標的專案 (s) 將需要條件式編譯符號，然後可用來派生程式碼以使用不同的 Api。 您可以在 [專案屬性] 頁面中設定條件式編譯符號，如下列影像所示：

![設定條件式編譯符號](media/update-visual-studio-extension/conditional-compilation-symbols.png)

請務必設定 *所有* 設定的編譯符號，因為根據預設，您輸入的符號只會套用至一個設定。

### <a name="c-techniques"></a>C \# 技術

然後，您可以使用該符號做為前置處理器指示詞 (`#if`) ，如下列程式碼所示。 然後您可以派生程式碼，以處理不同 Visual Studio 版本之間的重大變更。

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
#if Visual Studio 2019
    shell.LoadUILibrary(myGuid, myFlags, out uint ptrLib);
#else
    shell.LoadUILibrary(myGuid, myFlags, out IntPtr ptrLib);
#endif
```

在某些情況下，您可以直接使用 `var` 來避免命名類型，以避免需要 `#if` 區域。 上述程式碼片段也可以撰寫為：

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
    shell.LoadUILibrary(myGuid, myFlags, out var ptrLib);
```

使用語法時 `#if` ，請注意您如何使用下圖所示的語言服務內容下拉式清單來變更語法醒目提示，以及語言服務提供的其他説明，讓您在擴充功能與另一個目標 Visual Studio 版本上專注注意。

![共用專案中的條件式編譯](media/update-visual-studio-extension/conditional-compilation-if-region.png)

### <a name="xaml-sharing-techniques"></a>XAML 共用技術

XAML 沒有可讓您根據預處理器符號自訂內容的預處理器。 複製和維護兩個 XAML 頁面，其中的內容在 Visual Studio 2022 與較舊版本之間必須有不同的需求。

不過，在某些情況下，透過移除參考元件的命名空間，可以在一個 XAML 檔案中表示存在於 Visual Studio 2022 與較舊版本的不同元件中的類型參考：

```diff
-xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
-Value="{DynamicResource {x:Static vsui:TreeViewColors.SelectedItemActiveBrushKey}}"
+Value="{DynamicResource TreeViewColors.SelectedItemActiveBrushKey}"
```

## <a name="test-your-extension"></a>測試您的延伸模組

若要測試以 Visual Studio 2022 為目標的延伸模組，您必須安裝 Visual Studio 2022 Preview。
在 Visual Studio 2022 Preview 之前，您將無法在 Visual Studio 版本上執行64位延伸模組。

無論您的延伸模組是以 Visual Studio 2022 或較舊版本為目標，您都可以使用 Visual Studio 2022 Preview 來建立並測試您的延伸模組。 從 Visual Studio 2022 啟動 VSIX 專案時，將會啟動 Visual Studio 的實驗實例。

強烈建議您測試每個您想要延伸模組支援的 Visual Studio 版本。

現在您已準備好 [發佈您的延伸](#publish-your-extension)模組。

## <a name="publish-your-extension"></a>發佈您的擴充功能

很好，您已將 Visual Studio 2022 目標新增至擴充功能並加以測試。 現在您已準備好要發佈此延伸模組，讓世界 admire。

### <a name="visual-studio-marketplace"></a>Visual Studio Marketplace

將您的延伸模組發佈至 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 是讓新使用者尋找和安裝您的擴充功能的絕佳方式。 無論您的延伸模組是以獨佔方式 Visual Studio 2022，還是以較舊的 VS 版本為目標，Marketplace 都能為您提供支援。

未來，Marketplace 可讓您將多個 VSIXs 上傳至一個 Marketplace 清單，讓您上傳 Visual Studio 2022 目標的 VSIX 和預先 Visual Studio 的 2022 VSIX。 使用 VS 延伸模組管理員時，您的使用者將會自動取得已安裝之 VS 版本的正確 VSIX。

在 Visual Studio 2022 的預覽版本中，Marketplace 將只支援每個 Marketplace 清單的單一 VSIX 檔案。 雖然 Visual Studio 2022 處於預覽狀態，但建議您為您的延伸模組提供個別的 Visual Studio 2022 專用 Marketplace 清單。 如此一來，您就可以視需要逐一查看您的 Visual Studio 2022 擴充功能，而不會影響舊版 Visual Studio 的客戶。 您也可以將延伸模組標示為「預覽」，以設定預期它可能較不可靠，即使該程度的來源 Visual Studio 2022 （而不是您的主流延伸模組）。

### <a name="custom-installer"></a>自訂安裝程式

如果您建立 MSI/EXE 以安裝您) 的延伸模組，並產生 vsixinstaller.exe，以安裝延伸模組的 (部分，請注意 Visual Studio 2022 中的 VSIX 安裝程式已更新。 開發人員必須使用 Visual Studio 2022 隨附的 VSIX 安裝程式版本，將擴充功能安裝到 Visual Studio 2022。 Visual Studio 2022 中的 VSIX 安裝程式也會安裝適用的擴充功能，其目標為與相同電腦上的 Visual Studio 2022 並存安裝的舊版 Visual Studio。

### <a name="network-share"></a>網路共用

您可以透過 LAN 或任何其他方式共用您的延伸模組。 如果您的目標是 Visual Studio 2022 和預先 Visual Studio 2022，您將需要個別共用多個 VSIXs，並為其提供檔案名 (或將其放在唯一的資料夾) ，以協助您的使用者根據已安裝的 Visual Studio 版本，知道要安裝的 VSIX。

### <a name="other-considerations"></a>其他考量

#### <a name="dependencies"></a>相依性

如果您的 VSIX 透過元素將另一個 VSIX 指定為相依性 `<dependency>` ，則每個參考的 vsix 都必須安裝在與 vsix 相同的目標和產品架構中。 如果相依的 VSIX 不支援 Visual Studio 的目標安裝，則您的 VSIX 將會失敗。 相依 VSIX 可支援比您更多的目標和架構，而不是比較少。 這項限制表示 VSIX 與相依性的部署和散發方法應該鏡像其相依性。

## <a name="q--a"></a>問答集

**問**：我的延伸模組不需要任何 interop 變更，因為它只會提供資料 (例如) 的範本，我可以建立一個包含 Visual Studio 2022 的延伸模組嗎？

**答**：是！  如需詳細資訊，請參閱 [擴充功能而不](#extensions-without-running-code) 執行程式碼。

**問**： NuGet 相依性會帶入舊的 interop 元件，並導致衝突類別。

**答**：將下列程式程式碼新增至 .csproj 檔案，以避免重複的元件：

```xml
    <PackageReference Include="<Name of offending assembly>" ExcludeAssets="compile" PrivateAssets="all" />
```

這可防止封裝參考從其他相依性匯入舊版元件。

**問**：我的命令和快速鍵在將原始檔切換至共用的專案之後，Visual Studio 中無法運作。

**答**：「影像優化程式」範例的 [步驟 2.4](samples.md#step-2---refactor-source-code-into-a-shared-project) 示範如何將 .vsct 檔案新增為連結的專案，以便將它們編譯成 .vsct 檔案。

## <a name="next-steps"></a>後續步驟

遵循 [ImageOptimizer](samples.md)的逐步範例，並連結至專案，以及每個步驟的程式碼變更。
