---
title: 方案 (。Sln) 檔案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73d6f7fb83e9420f59122135761ce44ea641fe57
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="solution-sln-file"></a>方案 (。Sln) 檔案
解決方案是用於組織專案在 Visual Studio 中的結構。 方案會維護文字為基礎 (共用） 的.sln 和.suo （二進位檔、 使用者特定解決方案的選項） 檔案中的專案狀態資訊。 如需.suo 檔案的詳細資訊，請參閱[方案使用者選項 (。Suo) 檔案](../../extensibility/internals/solution-user-options-dot-suo-file.md)。  
  
 如果載入 VSPackage 的.sln 檔案中所參考的結果，環境會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>.sln 檔中讀取。  
  
 .Sln 檔案包含以文字為基礎的資訊，環境會使用來尋找並載入保存的資料和它所參考的 Vspackage 專案的名稱 / 值參數。 當使用者開啟方案時，環境會不斷循環`preSolution`， `Project`，和`postSolution`在方案中，專案載入方案的.sln 檔案中的資訊和保存的任何資訊附加至方案。  
  
 每個專案檔會包含讀取的環境，以填入與該專案的項目階層的其他資訊。 階層資料持續性是由專案; 控制資料不儲存在.sln 檔案中，雖然您可以刻意專案資訊寫入.sln 檔如果您選擇這樣做。 與持續性相關的詳細資訊，請參閱[專案持續性](../../extensibility/internals/project-persistence.md)和[開啟和儲存的專案項目](../../extensibility/internals/opening-and-saving-project-items.md)。  
  
## <a name="solution-file-contents"></a>方案檔案的內容  
 .Sln 檔案包含的數個區段，如下列程式碼所示。  
  
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
  
 若要載入的方案，環境會執行下列工作順序。  
  
1.  環境讀取.sln 檔案的全域區段，並處理標記的所有區段`preSolution`。 在此情況下，還有一個這類陳述式：  
  
    ```  
    GlobalSection(SolutionConfiguration) = preSolution  
         ConfigName.0 = Debug  
         ConfigName.1 = Release  
    ```  
  
     當環境讀取`GlobalSection('name')`標記，它將名稱對應至使用登錄 VSPackage。 索引鍵的名稱應該存在於登錄中 [HKLM\\< 應用程式識別碼的登錄根目錄\>\SolutionPersistence\AggregateGUIDs]。 金鑰的預設值為 VSPackage 寫入項目封裝的 GUID (REG_SZ)。  
  
2.  環境載入 VSPackage，呼叫`QueryInterface`的 vspackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>介面，並呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>方法 > 一節讓 VSPackage 可以將資料儲存中的資料。 環境會針對每個重複此程序`preSolution`> 一節。  
  
3.  環境逐一查看專案持續性區塊。 在此情況下，沒有一個專案。  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
    "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
    EndProject  
    ```  
  
     這個陳述式包含唯一的專案 GUID 和專案類型的 GUID。 環境會用這項資訊來尋找屬於方案的專案檔案，VSPackage 所需的每個專案。 專案 GUID 會傳遞至<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>載入特定的專案相關的 VSPackage，然後在專案載入的 VSPackage。 在此情況下，VSPackage，載入這個專案會為 Visual Basic。  
  
     每個專案可以保存有唯一的專案執行個體識別碼，使它可以視需要在方案中其他專案存取。 在理想情況下，如果方案和專案原始程式碼控制之下，專案的路徑應該相對於方案的路徑。 第一次載入方案時，專案檔無法在使用者電腦上。 有相對於方案檔案伺服器上儲存的專案檔案，是相當簡單的專案檔以便可以找到並複製到使用者的電腦。 然後將複製並載入其餘的專案所需的檔案。  
  
4.  根據.sln 檔案的專案區段中所包含的資訊，則環境會載入每個專案檔。 在專案本身負責然後填入專案階層架構，並載入任何巢狀的專案。  
  
5.  .Sln 檔案的所有區段都處理之後，解決方案會顯示在 [方案總管] 中，並可供使用者修改。  
  
 如果任何 VSPackage 實作專案方案中，無法載入，<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A>方法呼叫而且每個方案中的其他專案有機會來忽略它可能會在載入期間所做的變更。 如果剖析錯誤發生，請盡可能最多資訊會保留的方案檔，環境會顯示一個對話方塊，警告使用者方案已損毀。  
  
 儲存或關閉，方案時<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A>方法呼叫並傳遞至階層，以確認變更是否已對方案中，必須輸入到.sln 檔案。 Null 值，傳遞至`QuerySaveSolutionProps`中<xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>，表示方案保存資訊。 如果值不是 null，保存的資訊是針對特定的專案，取決於指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>介面。  
  
 如果沒有要儲存資訊<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>介面的指標呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A>方法。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>然後會呼叫方法來擷取名稱 / 值組，從環境`IPropertyBag`介面，並將資訊寫入.sln 檔案。  
  
 `SaveSolutionProps` 和`WriteSolutionProps`物件擷取資訊以從儲存環境會呼叫以遞迴方式`IPropertyBag`介面直到所有變更已都輸入的.sln 檔案。 如此一來，您可以確保方案和可用下次開啟方案時，會保存資訊。  
  
 每個載入的 VSPackage 會列舉，看看是否有任何項目將儲存到.sln 檔案。 它是只在會查詢登錄機碼的載入時間。 因為它們是在記憶體中儲存的解決方案時，環境會知道有關的所有載入封裝。  
  
 .Sln 檔案包含中的項目`preSolution`和`postSolution`區段。 因為解決方案需要這項資訊來正確載入.suo 檔案中沒有類似的區段。 .Suo 檔案包含使用者特定的選項，例如，不是共用或放置在原始程式碼控制之下的私人資訊。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [方案使用者選項 (。Suo) 檔案](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [方案](../../extensibility/internals/solutions.md)