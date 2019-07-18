---
title: HOW TO：開啟專案特定的編輯器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2439a07f63b8da854ca8dc331d26e30f49503257
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435933"
---
# <a name="how-to-open-project-specific-editors"></a>HOW TO：開啟專案特定的編輯器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果在開啟的專案項目檔本質上繫結至特定的編輯器中為該專案，專案必須使用專案特定編輯器開啟檔案。 檔案無法委派到 IDE 的機制，來選取一個編輯器。 比方說，而不是使用標準的點陣圖編輯器中，您可以使用此專案特定編輯器選項來指定特定的點陣圖編輯器可辨識對您的專案是唯一的檔案中的資訊。  
  
 IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>時它會判斷特定的專案應該開啟檔案的方法。 如需詳細資訊，請參閱 <<c0> [ 使用 開啟檔案命令顯示檔案](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)。 使用下列指導方針來實作`OpenItem`方法中，使您的專案使用的專案特定編輯器開啟檔案。  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>若要實作的專案特定編輯器 OpenItem 方法  
  
1. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法 (RDT_EditLock) 來判斷是否已開啟的檔案 （文件資料物件）。  
  
    > [!NOTE]
    > 如需有關文件資料和文件檢視物件的詳細資訊，請參閱[文件資料和自訂編輯器中的文件檢視](../extensibility/document-data-and-document-view-in-custom-editors.md)。  
  
2. 如果檔案已經開啟，請藉由呼叫 resurface 檔案<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>方法並指定值的 IDO_ActivateIfOpen`grfIDO`參數。  
  
     如果檔案已開啟，且所呼叫的專案以外的專案擁有文件，則會顯示警告，開啟 「 編輯器 」 是另一個專案中的使用者。 然後顯示 [檔案] 視窗。  
  
3. 如果您文字的緩衝區 （文件資料物件） 已經開啟，且您想要附加至另一個檢視，您必須負責連結該檢視。 從專案中，產生的檢視 （文件檢視物件） 的建議的方法如下所示：  
  
    1. 呼叫`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>服務，來取得變數的指標，<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>介面。  
  
    2. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>方法用來建立文件檢視類別的執行個體。  
  
4. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>方法，並指定您的文件檢視物件。  
  
     這個方法網站文件視窗中的文件檢視物件。  
  
5. 執行其中一個適當地呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A>或<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A>方法。  
  
     此時，檢視必須是完全初始化並準備好開啟。  
  
6. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>方法來顯示，並開啟檢視。  
  
## <a name="see-also"></a>另請參閱  
 [開啟和儲存專案項目](../extensibility/internals/opening-and-saving-project-items.md)   
 [如何：開啟標準編輯器](../extensibility/how-to-open-standard-editors.md)   
 [如何：針對開啟的文件開啟編輯器](../extensibility/how-to-open-editors-for-open-documents.md)
