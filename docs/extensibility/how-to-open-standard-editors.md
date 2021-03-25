---
title: 如何：開啟標準編輯器 |Microsoft Docs
description: 瞭解如何使用標準編輯器來執行 OpenItem 方法。 IDE 會針對指定的檔案類型決定標準編輯器。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1b0de198e96ff268a0744a4a97a4a160c585af9c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069903"
---
# <a name="how-to-open-standard-editors"></a>如何：開啟標準編輯器
當您開啟標準編輯器時，您可以讓 IDE 為指定的檔案類型決定標準編輯器，而不是為檔案指定專案特定的編輯器。

 完成下列程式以執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 方法。 這會在標準編輯器中開啟專案檔。

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>使用標準編輯器來執行 OpenItem 方法

1. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> (`RDT_EditLock`) 來判斷檔資料物件檔案是否已開啟。

2. 如果檔案已經開啟，請呼叫方法來 resurface 檔案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> ，為參數指定的值 `IDO_ActivateIfOpen` `grfIDO` 。

     如果檔案是開啟的，而且檔是由與呼叫專案不同的專案所擁有，您的專案就會收到一則警告，指出開啟的編輯器是來自另一個專案。 接著會顯示 [檔案] 視窗。

3. 如果檔未開啟或不在執行中的檔資料表中，請呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法 (`OSE_ChooseBestStdEditor`) 來開啟檔案的標準編輯器。

     當您呼叫方法時，IDE 會執行下列工作：

    1. IDE 會掃描登錄中的 editor/{guidEditorType}/Extensions 子機碼，以判斷哪一個編輯器可以開啟檔案，而且有最高的優先順序來進行這項操作。

    2. IDE 判斷出可以開啟檔案的編輯器之後，IDE 就會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 。 編輯器的實作為此方法的實，會傳回 IDE 呼叫和建立新開啟的檔所需的資訊 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> 。

    3. 最後，IDE 會使用一般的持續性介面（例如）載入檔 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 。

    4. 如果 IDE 之前判斷出階層或階層專案可供使用，IDE 會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> 在專案上呼叫方法，以取得專案層級內容指標， <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> 方法呼叫傳回。

4. <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> 如果您想要讓編輯器取得專案的內容，則在 ide 呼叫專案時，會將指標傳回至 ide。

     執行此步驟可讓專案提供其他服務給編輯器。

     如果檔視圖或檔視圖物件已成功放置於視窗框架中，則會藉由呼叫來初始化物件的資料 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A> 。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [開啟和儲存專案專案](../extensibility/internals/opening-and-saving-project-items.md)
- [如何：開啟專案特定的編輯器](../extensibility/how-to-open-project-specific-editors.md)
- [如何：開啟開啟檔的編輯器](../extensibility/how-to-open-editors-for-open-documents.md)
- [使用開啟檔案命令顯示檔案](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
