---
title: 新增項目加入新項目對話方塊 |Microsoft Docs
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
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a421ba2278c177eeb0fdba8571497e50ba71b39
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894231"
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>將項目新增至新增項目對話方塊
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

加入項目至的程序**加入新項目**對話方塊開頭的登錄機碼。 下列的登錄項目所示，AddItemTemplates 區段包含可在哪些項目中的目錄的名稱與路徑**加入新項目**放 對話方塊。  
  
> [!NOTE]
>  資料表的正後方的程式碼片段包含其他資訊的登錄項目。  
  
 此區段位於 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects]。  
  
 第一個 GUID 是這種; 專案的 CLSID第二個 GUID 指出新增的項目範本的已註冊的專案類型。  
  
 \\{C061DB26-5833-11D2-96F5-000000000000} \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \1  
  
 @="#6"  
  
 「 TemplatesDir"="\<Visual Studio SDK 安裝路徑\\\VSIntegration\\\SomeFolder\\\SomePackage\\\SomeProject\\\SomeProjectItems"  
  
 「 SortPriority"= dword:00000064  
  
|名稱|類型|（從.rgs 檔案） 的資料|描述|  
|----------|----------|-----------------------------|-----------------|  
|@ （預設值）|REG_SZ|#%IDS_ADDITEM_TEMPLATES_ENTRY %|資源識別碼**加入項目**範本。|  
|Val TemplatesDir|REG_SZ|%TEMPLATE_PATH%\SomeProjectItems|在對話方塊中顯示的專案項目路徑**加入新項目**精靈。|  
|Val SortPriority|REG_DWORD|100 ([!INCLUDE[vcprx64](../../includes/vcprx64-md.md)])|判斷樹狀節點中顯示的檔案中的排序次序**加入新項目** 對話方塊。|  
  
> [!NOTE]
>  Visual C# 和 Visual Basic 專案類型 GUID，如下所示的：[!INCLUDE[csprcs](../../includes/csprcs-md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 目錄列 TemplateDirs，也就是 %template_path%\someprojectitems，是節點的左側**加入新項目**對話方塊方塊中的樹狀結構。 在樹狀目錄中的其他項目為基礎的根目錄中的子目錄。 可加入至專案的檔案是在右窗格中的項目**加入新項目** 對話方塊。  
  
 一般而言，這個資料夾將包含範本檔案為您的專案，例如 HTML 的範本或.cpp 檔案中，以及任何.vsz 檔案來啟動精靈。 若要控制的項目顯示的方式，您也可以包含.vsdir 檔案將當地語系化的目錄名稱和圖示。 當地語系化的字串會出現在對話方塊中，表示此節點在樹狀目錄中加入新項目 對話方塊的標題。  
  
 不過，您不必擁有的所有項目一個.vsdir 檔案中。 您可以有一個.vsdir 檔案的目錄中的每個項目。 如需詳細資訊，請參閱[精靈 (。在 Vsz) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)和[範本目錄描述 (。Vsdir) 檔案](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)。  
  
> [!NOTE]
>  範本目錄中的.vsdir 檔案是選擇性的。 如果您只想要將專案項目放在目錄中，並顯示在**加入新項目** 對話方塊中，您可以將檔案放在 TemplatesDir 陳述式中指定的範本目錄中。 在右窗格中會顯示檔案**加入新項目**該專案的對話方塊。 不過，如果您想要顯示的檔案或圖示的當地語系化的標題，您必須包含至少一個.vsdir 檔案範本目錄中。  
  
## <a name="grouping-project-items"></a>群組的專案項目  
 如果您想要包含在資料夾中的樣板群組**加入新項目**對話方塊方塊樹狀目錄中，您必須使用項目範本根目錄底下的子目錄中。 當**加入新項目**對話方塊會顯示給使用者，他們也會看到子資料夾，並可以從中選取專案項目。  
  
 在程式碼區段之排序優先順序會決定相對於其他元素樹狀節點的樹狀目錄中建立此範本目錄的位置。 針對**加入新項目** 對話方塊之排序優先順序是所有您必須包含您的項目將會顯示在對話方塊中正確的位置。  
  
 您也可以實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>介面，以篩選中所顯示的內容**加入新項目** 對話方塊。 藉由實作這個介面，您可以設定一個範本目錄，例如包含的磁碟上 50 的範本和精靈檔案。 如此一來，您可以使用隸屬於某個專案類型、 其他 30 檔案屬於另一個專案類型，以及可用在專案的一般型別中的所有檔案的 20 個檔案的不同專案類型。 在這種方式，根據哪個專案建立範本，您可以顯示一組不同的範本檔案。  
  
 例如，如果在 Visual Basic 專案中，您可能會有 Web 專案和用戶端專案。 不是一個有用的項目新增至用戶端專案中，web form 和 windows form 不會很有用的項目加入至 Web 伺服器專案。 因此，您可以建立一個包含這兩種專案類型的所有檔案的範本目錄。 然後藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>，您可以隱藏的項目不會顯示根據專案或專案中的專案設定的類型。  
  
## <a name="filtering-project-items"></a>篩選的專案項目  
 `IVsFilterAddProjectItemDlg2` 提供下列方式篩選樹狀目錄 （左窗格） 專案檔 （右窗格） 中的項目：  
  
- 當地語系化的名稱 （.vsdir 檔案所包含的對話方塊中顯示的標題） 來提供`IVsFilterAddProjectItemDlg`。  
  
- 實際名稱的檔案和磁碟上的資料夾 (非當地語系化 — 任何.vsdir 檔案) 所提供`IVsFilterAddProjectItemDlg`。  
  
- 依類別、 提供`IVsFilterAddProjectItemDlg2`。  
  
  若要依類別篩選，提供項目在.vsdir 檔案中，例如 「 Web 表單 」 或 「 用戶端項目 」，在 Visual Basic 中的類別目錄字串。 對話方塊程式碼再擷取.vsdir 檔案中的類別目錄分類，並將它傳遞給您。 然後，您可以將該資訊傳遞您實作`IVsFilterAddProjectItemDlg2`來篩選**加入新項目**對話方塊中，依類別分組。 為 Web 網頁或用戶端 Win32 應用程式的情況下，您也可以篩選項目。 此外，您可以識別[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]標示 Microsoft Foundation Classes (MFC) 或使用中的範本程式庫 (ATL) 項目中的項目。 當您識別這些項目時，專案系統可以定義自己的分類，以便系統可以根據類別和分類篩選。  
  
  如果您實作此篩選器功能時，您不必將對應的每個項目應該隱藏資料表。 您只要可以分類為類型的項目，並放在.vsdir 檔案或檔案的分類。 然後您可以隱藏任何實作介面中有某個特定分類的項目。 如此一來，您可以進行中的項目**加入新項目**對話方塊方塊動態根據專案中的狀態。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Catid 通常用來擴充專案的物件](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [範本目錄描述 (。Vsdir) 檔案](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

