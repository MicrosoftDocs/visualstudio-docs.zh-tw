---
title: 如何:打開特定於項目的編輯器 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 3cb6e360a38d64de4976f83b0167d47dc03fbc87
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710846"
---
# <a name="how-to-open-project-specific-editors"></a>如何:開啟特定於項目的編輯器
如果專案正在打開的項檔本質上是綁定到該專案的特定編輯器的,則專案必須使用特定於專案的編輯器打開該檔。 檔不能委派給 IDE 選擇編輯器的機制。 例如,可以使用特定於專案的編輯器來指定特定的位圖編輯器,該編輯器可識別專案中唯一的資訊,而不是使用標準位圖編輯器。

 當 IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>確定特定專案應打開檔時,它調用該方法。 關於詳細資訊,請參考[檔案指令顯示檔案](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)。 使用以下準則實現`OpenItem`使用特定於專案的編輯器使專案打開檔的方法。

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>使用特定於項目的編輯器來提供 OpenItem 方法

1. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法`RDT_EditLock`( ) 以確定檔案 (文件資料物件) 是否已打開。

    > [!NOTE]
    > 關於文件資料與文件檢視物件的詳細資訊,請參考[自訂編輯器中的文件資料與文件檢視](../extensibility/document-data-and-document-view-in-custom-editors.md)。

2. 如果檔已打開,則通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>方法並`grfIDO`為 參數指定IDO_ActivateIfOpen值來重新顯示該檔。

     如果文件處於打開狀態,並且文檔歸調用專案以外的專案所有,則向使用者顯示一條警告,指出正在打開的編輯器來自另一個專案。 然後,文件視窗將浮出水面。

3. 如果文本緩衝區(文檔數據物件)已打開,並且要附加另一個檢視,則負責連接該檢視。 建議從項目中實體化檢視(文件檢視物件)的方法如下:

    1. 調用`QueryService`<xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>服務以獲取指向介面<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>的指標。

    2. 調用<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>方法以創建文檔視圖類的實例。

4. 調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>方法,指定文檔檢視物件。

     此方法將文件檢視物件設置在文件視窗中。

5. 對<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A><xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A>或方法執行適當的調用。

     此時,視圖應完全初始化並準備打開。

6. 調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>方法以顯示並打開檢視。

## <a name="see-also"></a>另請參閱
- [開啟與儲存項目項目](../extensibility/internals/opening-and-saving-project-items.md)
- [如何:開啟標準編輯器](../extensibility/how-to-open-standard-editors.md)
- [如何:開啟開啟文件的編輯器](../extensibility/how-to-open-editors-for-open-documents.md)
