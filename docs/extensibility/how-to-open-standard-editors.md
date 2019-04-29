---
title: HOW TO：開啟標準編輯器 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f34a239628c3ed9e8bccaa8590cb22100d7d290f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62862910"
---
# <a name="how-to-open-standard-editors"></a>HOW TO：開啟標準編輯器
當您開啟標準編輯器時，您會讓判斷指定的檔案類型，而不是指定之檔案的專案特定編輯器的標準編輯器在 IDE。

 完成下列程序來實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>方法。 這會在標準編輯器中開啟專案檔。

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>若要實作的標準編輯器 OpenItem 方法

1. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>(`RDT_EditLock`) 來判斷是否已開啟的文件資料物件檔案。

2. 如果檔案已經開啟，請藉由呼叫 resurface 檔案<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>方法，並指定的值`IDO_ActivateIfOpen`如`grfIDO`參數。

     如果檔案已開啟文件擁有者不同的專案，比呼叫的專案，您的專案就會發出警告，所開啟的編輯器是從另一個專案。 然後顯示 [檔案] 視窗。

3. 如果未開啟文件或不在執行中的文件表格，呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法 (`OSE_ChooseBestStdEditor`) 以開啟該檔案的標準編輯器。

     當您呼叫方法時，IDE 會執行下列工作：

    1. IDE 會掃描編輯器 / {guidEditorType} / 擴充功能子機碼中登錄，以判斷哪一個編輯器可以開啟檔案，並具有最高的優先權，執行此動作。

    2. IDE 判斷哪一個編輯器可以開啟檔案後，IDE 就會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>。 編輯器的實作，這個方法傳回的資訊所需的呼叫 IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>和站台的新開啟的文件。

    3. 最後，在 IDE 的文件載入使用一般的持續性介面，例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>。

    4. 如果 IDE 先前決定的階層或階層項目可供使用，IDE 就會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>方法來取得專案層級內容的專案<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>入傳遞的指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>方法呼叫。

4. 傳回<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>ide 中，當 IDE 呼叫的指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>上您的專案，如果您想要讓您的專案從編輯器取得內容。

     執行此步驟可讓專案的供應項目其他服務的編輯器。

     如果文件檢視或文件檢視物件已成功地設置在視窗框架中，物件初始化它的資料藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [開啟和儲存專案項目](../extensibility/internals/opening-and-saving-project-items.md)
- [如何：開啟專案特定的編輯器](../extensibility/how-to-open-project-specific-editors.md)
- [如何：開啟編輯器開啟的文件](../extensibility/how-to-open-editors-for-open-documents.md)
- [使用 開啟檔案命令顯示檔案](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)