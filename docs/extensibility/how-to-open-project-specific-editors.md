---
title: 如何： 開啟專案的特定編輯器 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae2e634d36c13632619d01cc97d5726dc5576819
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129037"
---
# <a name="how-to-open-project-specific-editors"></a>如何： 開啟專案的特定編輯器
如果正在開啟專案項目檔在本質上繫結至該專案的特定編輯器，專案必須使用專案特定編輯器開啟檔案。 檔案無法委派到 IDE 的機制，來選取一個編輯器。 比方說，而不是使用標準的點陣圖編輯器，您可以使用此專案專屬編輯器選項指定的特定點陣圖編輯器會辨識唯一至您的專案檔中的資訊。  
  
 IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>方法時，它會判斷特定專案應該開啟檔案。 如需詳細資訊，請參閱[使用開啟的 [檔案] 命令顯示檔案](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)。 使用下列指導方針來實作`OpenItem`方法，讓您使用的專案特定編輯器開啟檔案的專案。  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>若要實作的專案特定編輯器的 OpenItem 方法  
  
1.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法 (RDT_EditLock) 來判斷是否已開啟的檔案 （文件資料物件）。  
  
    > [!NOTE]
    >  如需文件資料和文件檢視物件的詳細資訊，請參閱[文件資料，以及在自訂編輯器中的文件檢視](../extensibility/document-data-and-document-view-in-custom-editors.md)。  
  
2.  如果檔案已經開啟，請藉由呼叫 resurface 檔案<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>方法和指定的值是針對 IDO_ActivateIfOpen`grfIDO`參數。  
  
     如果已開啟的檔案，在文件擁有者是呼叫專案以外的專案，將會顯示警告，開啟編輯器 是從另一個專案的使用者。 然後顯示 [檔案] 視窗。  
  
3.  如果您的文字緩衝區 （文件資料物件） 已經開啟，而且您想要附加至另一個檢視，您必須負責該檢視連結。 從專案中，產生的檢視 （文件檢視物件） 的建議的方法如下所示：  
  
    1.  呼叫`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>服務，來取得指向<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>介面。  
  
    2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>方法來建立文件檢視類別的執行個體。  
  
4.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>方法，並指定您的文件檢視物件。  
  
     這個方法網站文件視窗中的文件檢視物件。  
  
5.  執行至適當地呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A>或<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A>方法。  
  
     此時，檢視應該完全初始化並準備好開啟。  
  
6.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>方法，以顯示並開啟檢視。  
  
## <a name="see-also"></a>另請參閱  
 [開啟並儲存專案項目](../extensibility/internals/opening-and-saving-project-items.md)   
 [如何： 開啟標準編輯器](../extensibility/how-to-open-standard-editors.md)   
 [如何︰針對開啟的文件開啟編輯器](../extensibility/how-to-open-editors-for-open-documents.md)