---
title: 如何:打開標準編輯器 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f42cfa64106acc41358568f4c8f6bca2cd1141fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710795"
---
# <a name="how-to-open-standard-editors"></a>如何:開啟標準編輯器
開啟標準編輯器時,允許 IDE 確定指定檔案類型的標準編輯器,而不是為檔案指定特定於專案的編輯器。

 完成以下過程以實作該<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>方法 。 這將在標準編輯器中打開專案檔。

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>使用標準編輯器來 OpenItem 方法

1. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>`RDT_EditLock`( ) 以確定文件資料物件檔是否已開啟。

2. 如果檔已打開,則通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>方法重新顯示檔,`IDO_ActivateIfOpen``grfIDO`為 參數指定值。

     如果文件處於打開狀態,並且文檔由與調用專案不同的專案所有,則專案將收到一條警告,指出正在打開的編輯器來自另一個專案。 然後,文件視窗將浮出水面。

3. 如果文件未打開或在正在運行的文件表中打開,請呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法()`OSE_ChooseBestStdEditor`以打開檔案的標準編輯器。

     呼叫 方法時,IDE 將執行以下任務:

    1. IDE 掃描註冊表中的編輯器/[guidEditorType]/擴展子鍵,以確定哪個編輯器可以打開該檔,並且具有執行此操作的最高優先順序。

    2. 在 IDE 確定哪個編輯器可以開啟此檔案後,IDE 將<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>呼叫 。 此方法的編輯器實現返回 IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>調用 新打開的文檔並進行網站所需的資訊。

    3. 最後,IDE 使用通常的持久性介面(<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>如) 載入文檔。

    4. 如果 IDE 以前確定層次結構或層次結構項可用,則 IDE 調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>專案上的方法,以<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>獲取專案級上下<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>文 指標以使用 方法調用傳遞。

4. 如果要讓<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>編輯器從專案中獲取上下文,則<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>當 IDE 調用專案時,返回指向 IDE 的指標。

     執行此步驟可以使專案向編輯器提供其他服務。

     如果文件檢視或文檔檢視物件已成功駐留在視窗框架中,則通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>使用其數據初始化該物件。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [開啟並儲存項目項目項目](../extensibility/internals/opening-and-saving-project-items.md)
- [如何:開啟特定於項目的編輯器](../extensibility/how-to-open-project-specific-editors.md)
- [如何:開啟開啟文件的編輯器](../extensibility/how-to-open-editors-for-open-documents.md)
- [使用「開啟檔案」指令顯示檔案](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
