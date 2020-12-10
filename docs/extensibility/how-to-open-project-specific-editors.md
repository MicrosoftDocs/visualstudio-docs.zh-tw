---
title: 如何：開啟 Project-Specific 編輯器 |Microsoft Docs
description: 瞭解如何使用專案特定的編輯器來執行 OpenItem 方法，讓專案可以開啟系結至該專案之編輯器的檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4cbba1f4d6cf0a2a5a45dd2999afa5bbf3443fca
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993779"
---
# <a name="how-to-open-project-specific-editors"></a>如何：開啟專案特定的編輯器
如果專案開啟的專案檔本質上系結至該專案的特定編輯器，則專案必須使用專案特定的編輯器來開啟檔案。 無法將檔案委派給 IDE 用來選取編輯器的機制。 例如，您可以使用這個專案特定的編輯器選項來指定特定的點陣圖編輯器，以辨識專案中唯一的資訊，而不是使用標準點陣圖編輯器。

 IDE 在判斷檔案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 應該由特定專案開啟時，會呼叫方法。 如需詳細資訊，請參閱 [使用開啟檔案命令顯示](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)檔案。 使用下列指導方針來執行 `OpenItem` 方法，讓您的專案使用專案特定的編輯器來開啟檔案。

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>若要使用專案特定的編輯器來執行 OpenItem 方法

1. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> 方法 (`RDT_EditLock`) ，以判斷檔 (檔資料物件) 是否已開啟。

    > [!NOTE]
    > 如需檔資料和檔視圖物件的詳細資訊，請參閱 [自訂編輯器中的檔資料和檔查看](../extensibility/document-data-and-document-view-in-custom-editors.md)。

2. 如果檔案已開啟，請呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 方法並指定參數的 IDO_ActivateIfOpen 值，以 resurface 檔案 `grfIDO` 。

     如果檔案是開啟的，而且檔是由呼叫專案以外的專案所擁有，則會向使用者顯示警告，指出開啟的編輯器是來自另一個專案。 接著會顯示 [檔案] 視窗。

3. 如果您的文字緩衝區 (檔資料物件) 已開啟，而您想要將另一個視圖附加到該物件，您必須負責連結該視圖。 從專案) 具現化視圖 (檔視圖物件的建議方法如下：

    1. 呼叫 `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> 服務以取得介面的指標 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> 。

    2. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 方法來建立檔視圖類別的實例。

4. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> 方法，並指定您的檔視圖物件。

     這個方法會在文件視窗中，以檔視圖物件為網站。

5. 對或方法執行適當的呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> 。

     此時，應該會將視圖完全初始化並準備好開啟。

6. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 方法以顯示並開啟此視圖。

## <a name="see-also"></a>另請參閱
- [開啟和儲存專案專案](../extensibility/internals/opening-and-saving-project-items.md)
- [如何：開啟標準編輯器](../extensibility/how-to-open-standard-editors.md)
- [如何：開啟開啟檔的編輯器](../extensibility/how-to-open-editors-for-open-documents.md)
