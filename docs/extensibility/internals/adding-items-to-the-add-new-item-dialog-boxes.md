---
title: 新增項目加入新項目對話方塊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d447090585a2314899bb2d6246c6fb450a9e767d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956045"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>將項目新增至 [加入新項目] 對話方塊
加入項目至的程序**加入新項目**對話方塊開頭的登錄機碼。 下列登錄項目中所示**AddItemTemplates**一節包含可在哪一個項目中的目錄名稱與路徑**加入新項目**放 對話方塊。  

> [!NOTE]
>  資料表的正後方的程式碼片段包含其他資訊的登錄項目。  

 本章節位於**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects**。

 第一個 GUID 是這種; 專案的 CLSID第二個 GUID 指出新增的項目範本的已註冊的專案類型：  

 **\\{C061DB26-5833-11D2-96F5-000000000000}\\AddItemTemplates\\TemplatesDir\\{ACEF4EB2-57CF-11D2-96F4-000000000000}\\1**

 **@** = #6 

 **TemplatesDir** = \\&lt;Visual Studio SDK 安裝路徑&gt;\\VSIntegration\\&lt;SomeFolder&gt; \\&lt;SomePackage&gt;\\&lt;SomeProject&gt;\\&lt;SomeProjectItems&gt;

 **SortPriority** = dword:00000064


| 名稱 | 類型 | 資料 (從 *.rgs*檔案) | 描述 |
|------------------|-----------| - | - |
| @ （預設值） | REG_SZ | #%IDS_ADDITEM_TEMPLATES_ENTRY % | 資源識別碼**加入項目**範本。 |
| Val TemplatesDir | REG_SZ | %Template_path\\&lt;SomeProjectItems&gt; | 在對話方塊中顯示的專案項目路徑**加入新項目**精靈。 |
| Val SortPriority | REG_DWORD | 100 ([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]) | 判斷樹狀節點中顯示的檔案中的排序次序**加入新項目** 對話方塊。 |

> [!NOTE]
>  Visual C# 和 Visual Basic 專案類型 GUID 如下所示： 
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  

 針對列出的目錄**TemplatesDir**，即*TEMPLATE_PATH %\\&lt;SomeProjectItems&gt;*，是在左邊的節點**新增新的項目**對話方塊方塊中的樹狀結構。 在樹狀目錄中的其他項目為基礎的根目錄中的子目錄。 可加入至專案的檔案是在右窗格中的項目**加入新項目** 對話方塊。  

 一般而言，這個資料夾將包含範本檔案，例如 HTML 範本專案或 *.cpp*檔案，以及任何 *.vsz*檔案來啟動精靈。 若要控制的項目顯示的方式，您也可以包含 *.vsdir*當地語系化目錄名稱和圖示的檔案。 當地語系化的字串會出現在對話方塊中，表示此節點中的標題**加入新項目**對話方塊方塊中的樹狀結構。  

 不過，您沒有將所有項目在其中一個 *.vsdir*檔案。 您可以有一個 *.vsdir*檔案的目錄中的每個項目。 如需詳細資訊，請參閱 < [Wizard (.vsz) 檔](../../extensibility/internals/wizard-dot-vsz-file.md)並[範本目錄描述 (.vsdir) 檔案](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)。  

> [!NOTE]
>  *.Vsdir*是選擇性的範本目錄中的檔案。 如果您只想要將專案項目放在目錄中，並顯示在**加入新項目** 對話方塊中，您可以將該檔案中指定的範本目錄置於**TemplatesDir**陳述式。 在右窗格中會顯示檔案**加入新項目**該專案的對話方塊。 不過，如果您想要顯示的檔案或圖示的當地語系化的標題，您必須包含至少一個 *.vsdir*範本目錄中的檔案。  

## <a name="group-project-items"></a>群組的專案項目  
 如果您想要包含在資料夾中的樣板群組**加入新項目**對話方塊方塊樹狀目錄中，您必須使用項目範本根目錄底下的子目錄中。 當**加入新項目**對話方塊會顯示給使用者，他們也會看到子資料夾，並可以從中選取專案項目。  

 在程式碼區段之排序優先順序會決定相對於其他元素樹狀節點的樹狀目錄中建立此範本目錄的位置。 針對**加入新項目** 對話方塊之排序優先順序是所有您必須包含您的項目將會顯示在對話方塊中正確的位置。  

 您也可以實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>介面，以篩選中所顯示的內容**加入新項目** 對話方塊。 藉由實作這個介面，您可以設定一個範本目錄，例如包含的磁碟上 50 的範本和精靈檔案。 如此一來，您可以使用隸屬於某個專案類型、 其他 30 檔案屬於另一個專案類型，以及可用在專案的一般型別中的所有檔案的 20 個檔案的不同專案類型。 在這種方式，根據哪個專案建立範本，您可以顯示一組不同的範本檔案。  

 例如，如果在 Visual Basic 專案中，您可能會有 Web 專案和用戶端專案。 不是一個有用的項目新增至用戶端專案中，web form 和 windows form 不會很有用的項目加入至 Web 伺服器專案。 因此，您可以建立一個包含這兩種專案類型的所有檔案的範本目錄。 然後，藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>，您可以隱藏的項目不會顯示根據專案或專案中的專案設定的類型。  

## <a name="filter-project-items"></a>篩選專案項目  
 `IVsFilterAddProjectItemDlg2` 提供下列方式篩選樹狀目錄 （左窗格） 專案檔 （右窗格） 中的項目：  

- 當地語系化的名稱 (包含在對話方塊中顯示的原文字幕 *.vsdir*檔案) 所提供`IVsFilterAddProjectItemDlg`。  

- 實際名稱的檔案和磁碟上的資料夾 (非當地語系化-沒有 *.vsdir*檔案) 所提供`IVsFilterAddProjectItemDlg`。  

- 依類別、 提供`IVsFilterAddProjectItemDlg2`。  

  若要依類別篩選，請提供 類別目錄字串中的項目 *.vsdir*檔案，例如*網頁表單*或是*用戶端項目*Visual Basic 中。 對話方塊程式碼，然後擷取類別目錄分類 *.vsdir*檔案，並將它傳遞給您。 然後，您可以將該資訊傳遞您實作`IVsFilterAddProjectItemDlg2`來篩選**加入新項目**對話方塊中，依類別分組。 為 Web 網頁或用戶端 Win32 應用程式的情況下，您也可以篩選項目。 此外，您可以識別[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]標示 Microsoft Foundation Classes (MFC) 或使用中的範本程式庫 (ATL) 項目中的項目。 當您識別這些項目時，專案系統可以定義自己的分類，以便系統可以根據類別和分類篩選。  

  如果您實作此篩選器功能時，您不必將對應的每個項目應該隱藏資料表。 您只可以分類為類型的項目，並將分類放在 *.vsdir*檔案。 然後您可以隱藏任何實作介面中有某個特定分類的項目。 如此一來，您可以進行中的項目**加入新項目**對話方塊方塊動態根據專案中的狀態。  

## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Catid 通常用來擴充專案的物件](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [將專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [範本目錄描述 (.vsdir) 檔案](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [精靈 (.vsz) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)