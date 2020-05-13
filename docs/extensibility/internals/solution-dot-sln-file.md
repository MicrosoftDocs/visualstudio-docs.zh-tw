---
title: 解決方案 (.Sln)檔案
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f4eee1f0a5e8371d239b3c33d10e1d9d7998095
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705322"
---
# <a name="solution-sln-file"></a>解決方案 (.sln) 檔案

解決方案是用於在 Visual Studio 中組織專案的結構。 該解決方案在兩個檔案中維護專案的狀態資訊:

- .sln 檔案(基於文字的共用)

- .suo 檔案(二進位、特定於使用者的解決方案選項)

有關 .suo 檔的詳細資訊,請參閱[解決方案使用者選項 (。Suo) 檔案](../../extensibility/internals/solution-user-options-dot-suo-file.md)。

如果 VSPackage 是在 .sln 檔中引用的結果載入的,則<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>環境將調用 .sln 檔中讀取。

.sln 檔包含環境用於查找和載入持久化資料和它引用的專案 VS 包的名稱值參數的基於文字的資訊。 當使用者打開解決方案時,環境會迴圈流`preSolution``Project`覽 .sln`postSolution`檔案中的資訊以載入解決方案、解決方案中的專案以及附加到解決方案的任何持久化資訊。

每個項目的檔都包含環境讀取的其他資訊,以便使用該專案的項填充層次結構。 層次結構數據持久性由專案控制。 數據通常不儲存在 .sln 檔中,儘管如果您選擇這樣做,則可以有意將專案資訊寫入 .sln 檔。 有關持久性的詳細資訊,請參閱[專案持久性](../../extensibility/internals/project-persistence.md)以及[開啟和儲存項目項目](../../extensibility/internals/opening-and-saving-project-items.md)。

## <a name="file-header"></a>標頭

.sln 檔案的標頭如下所示:

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
主要版本的 Visual Studio(最近)保存了此解決方案檔。 此資訊控制解決方案圖示中的版本號。

`VisualStudioVersion = 15.0.26730.15`\
完整版本的 Visual Studio(最近)保存了解決方案檔。 如果解決方案檔由具有相同主版本的較新版本的 Visual Studio 保存,則不會更新此值,以減少解決方案檔中的改動。

`MinimumVisualStudioVersion = 10.0.40219.1`\
可以打開此解決方案檔的可視化工作室的最小(最舊)版本。

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
主要版本的 Visual Studio(最近)保存了此解決方案檔。 此資訊控制解決方案圖示中的版本號。

`VisualStudioVersion = 16.0.28701.123`\
完整版本的 Visual Studio(最近)保存了解決方案檔。 如果解決方案檔由具有相同主版本的較新版本的 Visual Studio 保存,則不會更新此值,以減少檔中的改動。

`MinimumVisualStudioVersion = 10.0.40219.1`\
可以打開此解決方案檔的可視化工作室的最小(最舊)版本。

::: moniker-end

## <a name="file-body"></a>檔案本文

.sln 檔案的主體由標`GlobalSection`記 的幾個部分組成,如下所示:

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

要載入解決方案,環境將執行以下任務序列:

1. 環境讀取 .sln 檔的全域部分,並處理標`preSolution`記 的所有部分。 此範例中檔案中,有一個這樣的語句:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   當環境讀取標記時`GlobalSection('name')`,它將名稱映射到使用註冊表的 VSPackage。 密鑰名稱應存在於註冊表中[HKLM\\<应用程序 ID\>註冊表根 [解決方案持久性]聚合 GUIDs]下。 鍵的預設值是寫入條目的 VSPackage 的包 GUID(REG_SZ)。

2. 環境載入 VSPackage,呼`QueryInterface`<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>叫介面的 VSPackage,並在節中使用資料<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>呼叫 該方法,以便 VSPackage 可以儲存資料。 環境將為每個`preSolution`部分重複此過程。

3. 環境通過專案持久性塊進行遍發。 在這種情況下,有一個專案。

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   此語句包含唯一的專案 GUID 和專案類型 GUID。 環境使用此資訊查找屬於解決方案的專案檔或檔,以及每個專案所需的 VSPackage。 專案 GUID 傳遞<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>給以 載入與專案相關的特定 VS 包,然後由 VSPackage 載入專案。 在這種情況下,為此專案載入的 VS 套件是可視化基本。

   每個專案都可以保留一個唯一的專案實例 ID,以便解決方案中的其他專案可以根據需要存取它。 理想情況下,如果解決方案和專案處於原始程式碼控制之下,則專案的路徑應相對於解決方案的路徑。 首次載入解決方案時,專案檔不能位於使用者的電腦上。 通過將專案檔相對於解決方案檔存儲在伺服器上,找到專案檔並將其複製到使用者的計算機相對簡單。 然後,它複製並載入專案所需的其餘檔。

4. 根據 .sln 檔案的專案部分中包含的資訊,環境將載入每個專案檔。 然後,專案本身負責填充專案層次結構並載入任何嵌套專案。

5. 處理 .sln 檔案的所有部分後,解決方案將顯示在解決方案資源管理器中,並可供使用者修改。

如果實現解決方案中專案的任何 VSPackage 無法載入,則<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A>調用 該方法,並且解決方案中的每個其他專案都有機會忽略它在載入過程中可能所做的更改。 如果發生分析錯誤,解決方案檔將保留盡可能多的資訊,環境將顯示一個對話方塊,警告使用者解決方案已損壞。

儲存或關閉解決方案時,<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A>將調用該方法並將其傳遞給層次結構,以查看是否對需要輸入到 .sln 檔案中的解決方案進行了更改。 傳入`QuerySaveSolutionProps`到<xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>的 null 值 表示正在為解決方案持久化資訊。 如果值不為空,則持久化的資訊適用於特定專案,由指向介面的<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>指標確定。

如果有要保存的資訊<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>, 則使用指向<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A>方法的指標呼叫介面。 然後<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>,環境調用該方法,`IPropertyBag`從介面檢索名稱值對並將資訊寫入 .sln 檔。

`SaveSolutionProps`環境`WriteSolutionProps`遞迴地調用物件,以檢索要從介面保存的`IPropertyBag`資訊, 直到所有更改都輸入到 .sln 檔中。 通過這種方式,您可以確保資訊將保留到解決方案中,並在下次打開解決方案時可用。

將枚舉每個載入的 VSPackage 以查看它是否有要儲存到 .sln 檔案的東西。 只有在載入時查詢註冊表項。 環境知道所有載入的包,因為它們在保存解決方案時位於記憶體中。

只有 .sln 檔`preSolution``postSolution`包含 和 節中的條目。 .suo 檔中沒有類似的部分,因為解決方案需要此資訊才能正確載入。 .suo 檔包含使用者特定的選項,如專用註釋,這些選項不打算共用或置於原始程式碼控制之下。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [方案使用者選項檔 (.Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [方案](../../extensibility/internals/solutions-overview.md)
