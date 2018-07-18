---
title: 加入項目來加入新項目對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a24a6d531812a170768f8c100f14ad64ab1e68c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135062"
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>加入項目來加入新項目對話方塊
新增項目到的程序**加入新項目**對話方塊開頭的登錄機碼。 AddItemTemplates > 一節中所示的下列登錄項目，包含可在哪些項目中的目錄名稱與路徑**加入新項目**放 對話方塊。  
  
> [!NOTE]
>  後置程式碼片段的資料表會包含其他資訊的登錄項目。  
  
 此區段位於 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects]。  
  
 第一個 GUID 為專案，此類型的 CLSID第二個 GUID 表示新增的項目範本的已註冊的專案類型。  
  
 \\{C061DB26-5833-11D2-96F5-000000000000} \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \1  
  
 @="#6"  
  
 「 TemplatesDir"="\<Visual Studio SDK 安裝路徑\\\VSIntegration\\\SomeFolder\\\SomePackage\\\SomeProject\\\SomeProjectItems"  
  
 「 SortPriority"= dword:00000064  
  
|名稱|類型|（從.rgs 檔案） 的資料|描述|  
|----------|----------|-----------------------------|-----------------|  
|@ （預設值）|REG_SZ|#%IDS_ADDITEM_TEMPLATES_ENTRY %|資源識別碼**加入項目**範本。|  
|Val TemplatesDir|REG_SZ|%TEMPLATE_PATH%\SomeProjectItems|顯示的對話方塊中的專案項目路徑**加入新項目**精靈。|  
|Val SortPriority|REG_DWORD|100 ([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)])|決定排序順序中的樹狀結構節點中顯示的檔案**加入新項目** 對話方塊。|  
  
> [!NOTE]
>  在 Visual C# 和 Visual Basic 專案類型的 GUID 如下：[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 目錄會列出 TemplateDirs，這是 %template_path%\someprojectitems，為的節點上的左半部**加入新項目**對話方塊方塊的樹狀結構。 在樹狀目錄中的其他項目為基礎的根目錄中的子目錄。 可加入至專案的檔案是在右窗格中的項目**加入新項目** 對話方塊。  
  
 一般而言，這個資料夾將包含範本 HTML 或.cpp 檔案中，例如您專案的範本檔案和任何.vsz 檔案來啟動精靈。 若要控制的項目顯示的方式，您也可以包含.vsdir 當地語系化目錄名稱和圖示的檔案。 當地語系化的字串會出現在對話方塊中，表示此節點在樹狀目錄中加入新項目 對話方塊的標題。  
  
 不過，您不必具備一個.vsdir 檔案中所有元件。 您可以有一個.vsdir 檔案的目錄中的每個項目。 如需詳細資訊，請參閱[精靈 (。Vsz) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)和[範本目錄的描述 (。Vsdir) 檔案](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)。  
  
> [!NOTE]
>  .Vsdir 目錄中的檔案範本是選擇性的。 如果您只想要放在目錄中的專案項目，並顯示在**加入新項目**對話方塊中，您可以將檔案放在 TemplatesDir 陳述式中指定的範本目錄中。 檔案就會顯示在右窗格的**加入新項目**該專案的對話方塊。 不過，如果您想要顯示的檔案或圖示的當地語系化的標題，您必須包含至少一個.vsdir 檔案範本目錄中。  
  
## <a name="grouping-project-items"></a>群組的專案項目  
 如果您想要包含在資料夾中的範本群組**加入新項目**對話方塊方塊樹狀目錄中，您必須在其中的項目範本根目錄下的子目錄。 當**加入新項目**對話方塊會顯示給使用者，他們也會看到子資料夾及可以從中選取專案項目。  
  
 在程式碼區段之排序優先順序會決定相對於樹狀節點的其他項目樹狀目錄中建立此範本目錄的位置。 如**加入新項目**對話方塊中，排序優先順序為 all，使您的項目會顯示在正確的位置，在對話方塊中，您必須包含。  
  
 您也可以實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>來篩選顯示之內容的介面**加入新項目** 對話方塊。 實作這個介面，您可以設定一個範本的目錄，例如包含的磁碟 50 個範本和精靈的檔案。 如此一來，您可以使用隸屬於一個專案類型，其他 30 檔屬於另一個專案類型，與一般類型的專案中可用的所有檔案的 20 個檔案的不同專案類型。 在這種方式，根據哪個專案建立範本，您可以顯示一組不同的範本檔案。  
  
 例如，在 Visual Basic 專案中，您可能會有 Web 專案和用戶端專案。 Web form 不實用的項目新增至用戶端專案，而 windows form 不實用的項目加入至 Web 伺服器專案。 因此，您可以建立一個包含所有的這兩種類型的專案檔案的範本目錄。 然後藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>，您可以隱藏的項目不會顯示根據專案或專案中的專案設定的類型。  
  
## <a name="filtering-project-items"></a>篩選的專案項目  
 `IVsFilterAddProjectItemDlg2` 提供下列方式篩選的樹狀目錄 （左窗格） 專案檔 （右窗格） 中的項目：  
  
-   所提供的當地語系化名稱 （包含在.vsdir 檔案對話方塊中顯示的標題） `IVsFilterAddProjectItemDlg`。  
  
-   實際名稱的檔案和磁碟上的資料夾 (非當地語系化 — 沒有.vsdir 檔案) 所提供`IVsFilterAddProjectItemDlg`。  
  
-   依類別目錄，由`IVsFilterAddProjectItemDlg2`。  
  
 若要依類別篩選，請提供.vsdir 檔案，例如 [Web 表單] 中的項目或在 Visual Basic 中的 「 用戶端項目 」 的類別目錄字串。 對話方塊程式碼再擷取.vsdir 檔案中的類別目錄分類，並將其傳遞給您。 然後，您可以將該資訊傳遞至您的實作`IVsFilterAddProjectItemDlg2`篩選**加入新項目**對話方塊裡的類別。 Web 網頁或用戶端 Win32 應用程式的情況下，您也可以篩選項目。 此外，您可以識別[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]標記項目做為 Microsoft Foundation Classes (MFC) 或使用中的範本程式庫 (ATL) 項目。 當您識別這些項目時，專案系統，讓系統可以根據類別和分類篩選可以定義自己的分類。  
  
 如果您實作此篩選器功能時，您沒有對應的每個項目應該隱藏資料表。 您只可以將項目分類為類型，並置於.vsdir 或多個檔案的分類。 然後您可以隱藏任何實作介面中有某個特定分類的項目。 如此一來，您可以在中的項目**加入新項目**對話方塊方塊動態根據專案中的狀態。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [物件，通常會用來擴充專案項 Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [範本目錄的描述 (。Vsdir) 檔案](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)