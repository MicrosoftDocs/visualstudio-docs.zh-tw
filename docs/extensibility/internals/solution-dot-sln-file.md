---
title: 解決方案 (。.Sln) 檔案
description: 瞭解 .sln 檔案，這是在 Visual Studio 中維護專案之狀態資訊的其中一個檔案。
ms.custom: SEO-VS-2020
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27364382a7e4318fce822b148e9d3df6747bfd1e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081993"
---
# <a name="solution-sln-file"></a>方案 ( .sln) 檔

方案是在 Visual Studio 中組織專案的結構。 解決方案會在兩個檔案中維護專案的狀態資訊：

- .sln 檔案 (以文字為基礎的共用) 

- .suo 檔案 (二進位、使用者專用的解決方案選項) 

如需 .suo 檔案的詳細資訊，請參閱 [ ( 的方案使用者選項。.Suo) ](../../extensibility/internals/solution-user-options-dot-suo-file.md)檔案。

如果您的 VSPackage 因為 .sln 檔案中的參考而載入，則環境會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> .sln 檔案中的 read。

.Sln 檔案包含以文字為基礎的資訊，供環境用來尋找及載入保存資料的名稱值參數，以及它所參考的專案 Vspackage。 當使用者開啟方案時，環境會迴圈執行 .sln 檔案 `preSolution` 中的、 `Project` 和 `postSolution` 資訊，以載入解決方案、方案內的專案，以及附加至方案的任何保存資訊。

每個專案的檔案都包含環境所讀取的其他資訊，以便在階層中填入該專案的專案。 階層資料持續性是由專案所控制。 資料通常不會儲存在 .sln 檔案中，但如果您選擇這樣做，則可以刻意將專案資訊寫入 .sln 檔案。 如需持續性的詳細資訊，請參閱 [專案持續](../../extensibility/internals/project-persistence.md) 性和 [開啟和儲存專案專案](../../extensibility/internals/opening-and-saving-project-items.md)。

## <a name="file-header"></a>檔案標頭

.Sln 檔案的標頭如下所示：

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>定義

`Microsoft Visual Studio Solution File, Format Version 12.00`\
定義檔案格式版本的標準標頭。

`# Visual Studio 15`\
Visual Studio 的主要版本， (最近) 儲存此方案檔。 這項資訊會控制解決方案圖示中的版本號碼。

`VisualStudioVersion = 15.0.26730.15`\
Visual Studio 的完整版本， (最近) 儲存的方案檔。 如果解決方案檔是由具有相同主要版本的較新版本 Visual Studio 所儲存，則不會更新此值，以便減少解決方案檔中的流失情形。

`MinimumVisualStudioVersion = 10.0.40219.1`\
可以開啟此方案檔之 Visual Studio 的最小 () 版本。

::: moniker-end

::: moniker range=">=vs-2019"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio Version 16
VisualStudioVersion = 16.0.28701.123
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>定義

`Microsoft Visual Studio Solution File, Format Version 12.00`\
定義檔案格式版本的標準標頭。

`# Visual Studio Version 16`\
Visual Studio 的主要版本， (最近) 儲存此方案檔。 這項資訊會控制解決方案圖示中的版本號碼。

`VisualStudioVersion = 16.0.28701.123`\
Visual Studio 的完整版本， (最近) 儲存的方案檔。 如果解決方案檔是由具有相同主要版本的較新版本 Visual Studio 所儲存，則不會更新此值，以減少檔案中的流失情形。

`MinimumVisualStudioVersion = 10.0.40219.1`\
可以開啟此方案檔之 Visual Studio 的最小 () 版本。

::: moniker-end

## <a name="file-body"></a>檔案主體

.Sln 檔案的主體包含數個標示的區段 `GlobalSection` ，如下所示：

```
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
EndProject
Global
  GlobalSection(SolutionNotes) = postSolution
  EndGlobalSection
  GlobalSection(SolutionConfiguration) = preSolution
       ConfigName.0 = Debug
       ConfigName.1 = Release
  EndGlobalSection
  GlobalSection(ProjectDependencies) = postSolution
  EndGlobalSection
  GlobalSection(ProjectConfiguration) = postSolution
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86
  EndGlobalSection
  GlobalSection(ExtensibilityGlobals) = postSolution
  EndGlobalSection
  GlobalSection(ExtensibilityAddIns) = postSolution
  EndGlobalSection
EndGlobal
```

若要載入解決方案，環境會執行下列一系列的工作：

1. 環境會讀取 .sln 檔案的全域區段，並處理所有標示的區段 `preSolution` 。 在此範例檔案中，有一個此類語句：

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   當環境讀取標記時 `GlobalSection('name')` ，它會使用登錄將名稱對應至 VSPackage。 機碼名稱應該存在於 [HKLM \\<應用程式識別碼登錄根目錄 \SolutionPersistence\AggregateGUIDs] 底下的登錄中 \> 。 索引鍵的預設值是封裝 GUID (REG_SZ) 寫入專案的 VSPackage。

2. 環境會載入 VSPackage、 `QueryInterface` 針對介面呼叫 VSPackage， <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> 然後 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> 使用區段中的資料來呼叫方法，讓 VSPackage 可以儲存資料。 環境會針對每個區段重複此進程 `preSolution` 。

3. 環境會逐一查看專案持續性區塊。 在此案例中，有一個專案。

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   此語句包含唯一的專案 GUID 和專案類型 GUID。 環境會使用這項資訊來尋找屬於解決方案的專案檔或檔案，以及每個專案所需的 VSPackage。 專案 GUID 會傳遞至以 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> 載入與專案相關的特定 VSPackage，然後由 VSPackage 載入專案。 在此情況下，會 Visual Basic 為此專案載入的 VSPackage。

   每個專案都可以保存唯一的專案實例識別碼，以便在方案中依其他專案的需要來存取。 在理想的情況下，如果方案和專案是在原始程式碼控制之下，則專案的路徑應相對於方案的路徑。 第一次載入解決方案時，專案檔案不能在使用者的電腦上。 藉由將專案檔儲存在伺服器上的相對於方案檔，您就可以更輕鬆地找到專案檔並將其複製到使用者的電腦。 然後，它會複製並載入專案所需的其餘檔案。

4. 根據 .sln 檔案的 [專案] 區段中所包含的資訊，環境會載入每個專案檔。 專案本身負責擴展專案階層，並載入任何的嵌套專案。

5. 處理 .sln 檔案的所有區段之後，方案會顯示在方案總管中，並且可供使用者修改。

如果任何在解決方案中執行專案的 VSPackage 都無法載入，則 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> 會呼叫方法，而且方案中的每個其他專案都會有機會忽略可能在載入期間進行的變更。 如果發生剖析錯誤，解決方案檔會盡可能保留最多的資訊，而環境會顯示對話方塊，警告使用者解決方案已損毀。

當您儲存或關閉方案時， <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> 會呼叫方法並傳遞至階層，以查看是否已對需要輸入 .sln 檔案的方案進行變更。 傳入的 null 值 `QuerySaveSolutionProps` <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> 表示解決方案的資訊已保存。 如果此值不是 null，則會針對特定專案（由介面指標決定）保存的資訊 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 。

如果有要儲存的資訊，則 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> 會使用方法的指標來呼叫介面 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> 。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>然後，環境會呼叫方法，以從介面取出名稱/值組 `IPropertyBag` ，並將資訊寫入 .sln 檔案。

`SaveSolutionProps``WriteSolutionProps`環境會以遞迴方式呼叫和物件，以抓取要從介面儲存的資訊， `IPropertyBag` 直到所有變更都輸入 .sln 檔案中為止。 如此一來，您可以確保資訊會隨解決方案保存，並在下一次開啟解決方案時使用。

每個載入的 VSPackage 都會列舉，以查看是否有任何要儲存至 .sln 檔案的檔案。 只有在載入登錄機碼時，才會進行這項工作。 環境會知道所有載入的封裝，因為在儲存方案時，它們會在記憶體中。

只有 .sln 檔案包含和區段中的專案 `preSolution` `postSolution` 。 .Suo 檔案中沒有類似的區段，因為解決方案需要此資訊才能正確載入。 .Suo 檔案包含使用者特定的選項（例如私用備註），不適合在原始程式碼控制之下共用或放置。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [方案使用者選項檔 (.Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [方案](../../extensibility/internals/solutions-overview.md)
