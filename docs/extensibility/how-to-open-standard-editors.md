---
title: 如何：開啟標準編輯器 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c12e831654e7e138289d33b6e6f0409328e22c8c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905790"
---
# <a name="how-to-open-standard-editors"></a>如何：開啟標準編輯器
當您開啟標準編輯器時，您可以讓 IDE 判斷指定之檔案類型的標準編輯器，而不是指定檔案的專案特定編輯器。

 請完成下列程式，以執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 方法。 這會在標準編輯器中開啟專案檔。

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>若要使用標準編輯器來執行 OpenItem 方法

1. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> （ `RDT_EditLock` ），以判斷檔資料物件檔是否已開啟。

2. 如果檔案已開啟，請呼叫方法來 resurface 檔案，並 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 為參數指定的值 `IDO_ActivateIfOpen` `grfIDO` 。

     如果檔案已開啟，而且檔是由呼叫專案以外的其他專案所擁有，則您的專案會收到警告，表示開啟的編輯器來自另一個專案。 接著會顯示 [檔案] 視窗。

3. 如果檔未開啟或不在執行中的檔資料表中，請呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法（ `OSE_ChooseBestStdEditor` ）來開啟檔案的標準編輯器。

     當您呼叫方法時，IDE 會執行下列工作：

    1. IDE 會掃描登錄中的 editor/{guidEditorType}/Extensions 子機碼，以判斷哪一個編輯器可以開啟檔案，以及執行此動作的最高優先順序。

    2. 在 IDE 判斷哪些編輯器可以開啟檔案之後，IDE 會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 。 編輯器的這個方法的執行會傳回 IDE 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> 和網站新開啟的檔所需的資訊。

    3. 最後，IDE 會使用一般的持續性介面（例如）載入檔 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 。

    4. 如果 IDE 先前判斷出階層或階層專案可供使用，IDE 會在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> 專案上呼叫方法，以取得專案層級內容指標， <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 並傳回 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> 方法呼叫。

4. <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> 如果您想要讓編輯器從您的專案取得內容，請在 ide 呼叫您的專案時，傳回 ide 的指標。

     執行此步驟可讓專案提供編輯器的其他服務。

     如果已成功將檔視圖或檔視圖物件放置在視窗框架中，則會藉由呼叫，將物件初始化為其資料 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A> 。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [開啟和儲存專案專案](../extensibility/internals/opening-and-saving-project-items.md)
- [如何：開啟專案特定的編輯器](../extensibility/how-to-open-project-specific-editors.md)
- [如何：針對開啟的檔開啟編輯器](../extensibility/how-to-open-editors-for-open-documents.md)
- [使用 [開啟檔案] 命令顯示檔案](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
