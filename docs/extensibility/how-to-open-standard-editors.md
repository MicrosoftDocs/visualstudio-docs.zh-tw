---
title: "如何： 開啟標準編輯器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd3e3b8da06e6846c8c6adc6ddc3f65873c1e2bb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-open-standard-editors"></a>如何： 開啟標準編輯器
當您開啟標準編輯器時，您會讓 IDE 判斷指定的檔案類型，而不是指定之檔案的專案特定編輯器的標準編輯器。  
  
 完成下列程序來實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>方法。 這會在標準編輯器中開啟專案檔。  
  
### <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>若要使用標準編輯器實作 OpenItem 方法  
  
1.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>(`RDT_EditLock`) 來判斷是否已開啟的文件資料物件檔案。  
  
2.  如果檔案已經開啟，請藉由呼叫 resurface 檔案<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>方法，並指定值為`IDO_ActivateIfOpen`如`grfIDO`參數。  
  
     如果已開啟的檔案，在文件擁有者是不同的專案呼叫的專案，您的專案就會收到警告，開啟編輯器 是從另一個專案。 然後顯示 [檔案] 視窗。  
  
3.  如果尚未開啟文件或不在執行中的文件表格，呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法 (`OSE_ChooseBestStdEditor`) 檔案的標準編輯器開啟。  
  
     當您呼叫方法時，IDE 會執行下列工作：  
  
    1.  IDE 會掃描編輯器 / {guidEditorType} / 擴充功能子機碼中登錄，以判斷哪一個編輯器可以開啟檔案，並具有最高的優先權執行此作業。  
  
    2.  IDE 判定的編輯器都可以開啟檔案後，IDE 會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>。 編輯器的實作這個方法會傳回資訊所需的 IDE，才能呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>和站台的新開啟的文件。  
  
    3.  最後，在 IDE 的文件載入使用一般的持續性介面，例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>。  
  
    4.  如果 IDE 先前決定的階層或階層項目可供使用，IDE 便會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>方法來取得專案層級內容的專案上<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>指標傳遞回中<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>方法呼叫。  
  
4.  傳回<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>指標 IDE 當 IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>您的專案，如果您想要讓編輯器取得內容，從您的專案。  
  
     執行這個步驟可讓專案提供其他服務，與編輯器。  
  
     文件檢視或文件檢視物件已成功為基礎的視窗框架中，如果物件使用初始化資料呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [開啟並儲存專案項目](../extensibility/internals/opening-and-saving-project-items.md)   
 [如何： 開啟專案的特定編輯器](../extensibility/how-to-open-project-specific-editors.md)   
 [如何： 開啟編輯器開啟的文件](../extensibility/how-to-open-editors-for-open-documents.md)   
 [使用開啟檔案命令顯示檔案](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)