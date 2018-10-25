---
title: 方案 (。Sln) 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4bd3089d6916615a8b16d07b92b51f32afafaedc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886951"
---
# <a name="solution-sln-file"></a>方案檔 (.Sln)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

方案是組織專案在 Visual Studio 中的結構。 解決方案會保留在以文字為基礎 (共用） 的.sln 和.suo （二進位、 使用者特定的解決方案選項） 檔案中的專案的狀態資訊。 如需.suo 檔案的詳細資訊，請參閱[方案使用者選項 (。Suo) 檔案](../../extensibility/internals/solution-user-options-dot-suo-file.md)。  
  
 如果結果中而非.sln 檔案參考載入 VSPackage 時，環境會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>.sln 檔案中讀取。  
  
 而非.sln 檔案包含以文字為基礎的資訊，環境會使用來尋找並載入保存的資料和它所參考的 Vspackage 專案的名稱 / 值參數。 當使用者開啟解決方案時，環境會不斷循環`preSolution`， `Project`，和`postSolution`在方案中，專案的載入方案，而非.sln 檔案中的資訊，並保存的任何資訊附加至的方案。  
  
 每個專案的檔案會包含讀取的環境，以填入與該專案的項目階層的其他資訊。 階層的資料持續性是由專案; 控制資料不是通常儲存在.sln 檔案中上,，雖然您可以故意寫入專案資訊而非.sln 檔案如果您選擇這樣做。 與持續性的詳細資訊，請參閱[專案持續性](../../extensibility/internals/project-persistence.md)並[開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)。  
  
## <a name="solution-file-contents"></a>解決方案檔案的內容  
 而非.sln 檔案包含數個區段，如下列程式碼所示。  
  
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
  
1. 環境讀取而非.sln 檔案全域區段，並處理標記的所有區段`preSolution`。 在此情況下，還有一個這類陳述式：  
  
   ```  
   GlobalSection(SolutionConfiguration) = preSolution  
        ConfigName.0 = Debug  
        ConfigName.1 = Release  
   ```  
  
    當環境讀取`GlobalSection('name')`標記，它會將名稱對應到使用登錄 VSPackage。 在登錄中應有的機碼名稱 [HKLM\\< 應用程式識別碼的登錄根目錄\>\SolutionPersistence\AggregateGUIDs]。 機碼中的預設值為 VSPackage 所撰寫的項目封裝的 GUID (REG_SZ)。  
  
2. 環境載入 VSPackage，呼叫`QueryInterface`上的 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>介面，並呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>方法讓 VSPackage 可以儲存資料的一節中的資料。 環境會針對每個重複此程序`preSolution`一節。  
  
3. 環境逐一查看專案持續性區塊。 在此情況下，沒有一個專案。  
  
   ```  
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
   EndProject  
   ```  
  
    此陳述式包含唯一的專案 GUID 和專案類型 GUID。 環境會使用此資訊來尋找屬於方案的專案檔案和 VSPackage 所需的每個專案。 GUID 會傳遞至專案<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>載入特定的專案相關的 VSPackage，然後載入專案的 vspackage。 在此情況下，VSPackage 載入這個專案是 Visual Basic。  
  
    每個專案可以保存唯一的專案執行個體識別碼，以便它可以視需要存取由方案中其他專案。 在理想情況下，如果方案和專案是受原始程式碼控制，專案的路徑應相對於方案的路徑。 第一次載入方案時，無法在使用者電腦上的專案檔案。 擁有相對於方案檔案伺服器上所儲存的專案檔，就相當簡單之專案檔，找到並複製到使用者的電腦。 然後複製並載入其餘的專案所需的檔案。  
  
4. 根據.sln 檔案的 [專案] 區段中包含的資訊，則環境會載入每個專案檔。 在專案本身就負責填入專案階層架構，並載入任何巢狀的專案。  
  
5. 處理而非.sln 檔案的所有區段之後，解決方案會顯示在 [方案總管] 中，並可供使用者修改。  
  
   如果任何 VSPackage 實作專案方案中，無法載入，<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A>方法呼叫，而且方案中的每個專案有機會要略過它可能會在載入期間所做的變更。 如果發生剖析錯誤，盡可能最多資訊會保留的方案檔，並環境會顯示對話方塊，警告使用者方案已損毀。  
  
   當此解決方案不會儲存或關閉，<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A>方法呼叫並傳遞至該階層，查看是否已變更至要輸入而非.sln 檔案的方案。 為 null 的值，傳遞至`QuerySaveSolutionProps`在<xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>，指出資訊會被保存解決方案。 如果值不是 null，持續性的資訊是針對特定的專案，取決於指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>介面。  
  
   如果沒有資訊要儲存<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>介面的指標呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A>方法。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>然後會呼叫方法來擷取名稱 / 值組，從環境`IPropertyBag`介面，並將資訊寫入而非.sln 檔案。  
  
   `SaveSolutionProps` 並`WriteSolutionProps`物件會以遞迴方式呼叫擷取資訊以從儲存環境`IPropertyBag`介面之前所有的變更已輸入而非.sln 檔案。 如此一來，您可以確保方案和可用的下一次開啟方案時，將會保存的資訊。  
  
   每個載入的 VSPackage 會列舉，看看是否有任何內容，將儲存到.sln 檔案。 它是只在會查詢登錄機碼的載入時間。 因為它們是在記憶體中儲存方案時，環境會知道有關的所有載入的封裝。  
  
   而非.sln 檔案包含中的項目`preSolution`和`postSolution`區段。 因為解決方案需要這項資訊來正確載入.suo 檔案中沒有類似的區段。 .Suo 檔案包含使用者特定的選項，例如私用附註，不適合共用或放置在原始程式碼控制之下。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [方案使用者選項 (。Suo) 檔案](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [方案](../../extensibility/internals/solutions.md)

