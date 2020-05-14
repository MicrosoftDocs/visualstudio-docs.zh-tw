---
title: 支援多個文件檢視 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a952414fa7156d80675564e519e556ccedd524a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699544"
---
# <a name="supporting-multiple-document-views"></a>支援多個文件檢視
您可以透過編輯器建立單獨的文件資料和文件檢視物件來提供文件的多個檢視。 在附加文件檢視有用的一些情況下,有以下情況:

- 新的視窗支援:您希望編輯器提供兩個或多個相同類型的檢視,以便已在編輯器中打開視窗的使用者可以通過從 **「視窗」** 選單中選擇 **「新建視窗**」命令打開新視窗。

- 表單和程式碼檢視支援:您希望編輯器提供不同類型的檢視。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]例如,提供表單單檢視和代碼檢視。

  有關此的詳細資訊,請參閱 Visual Studio 包樣本建立的自訂編輯器專案中 EditorFactory.cs 檔中的 CreateEditorInstance 過程。 有關此項目的詳細資訊,請參閱[演練:建立自訂編輯器](../extensibility/walkthrough-creating-a-custom-editor.md)。

## <a name="synchronizing-views"></a>同步檢視
 實現多個檢視時,文檔數據物件負責使所有檢視與資料保持同步。 您可以使用<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>事件 處理介面將多個檢視與數據同步。

 如果不使用<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件同步多個檢視,則必須實現自己的事件系統來處理對文檔數據物件所做的更改。 您可以使用不同級別的粒度來使多個檢視保持最新。 使用最大粒度設置,當您在一個視圖中鍵入時,其他視圖將立即更新。 以最小的粒度,其他檢視在啟動之前不會更新它們。

## <a name="determining-whether-document-data-is-already-open"></a>確定文件資料是否已開啟
 集成開發環境 (IDE) 中的正在執行的文件表 (RDT) 可幫助追蹤文件的資料是否已打開,如下圖所示。

 ![文件資料檢視圖形](../extensibility/media/docdataview.gif "文件資料檢視")多個檢視

 預設情況下,每個檢視(文件檢視物件)都包含在其自己的視窗框架中 。<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 但是,如前所述,文檔數據可以顯示在多個檢視中。 為此,Visual Studio 會檢查 RDT 以確定有問題的文檔是否已在編輯器中打開。 當 IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>呼叫以建立編輯器`punkDocDataExisting`時, 參數中傳回的非 NULL 值指示文檔已在另一個編輯器中打開。 關於 RDT 如何工作的詳細資訊,請參考[文件表](../extensibility/internals/running-document-table.md)。

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>在實現中,檢查返回的文件數據物件`punkDocDataExisting`,以確定文件資料是否適合編輯器。 (例如,HTML 編輯器只能顯示 HTML 資料。如果合適,則編輯器工廠應為數據提供第二個檢視。 如果`punkDocDataExisting`參數`NULL`不是 ,則文檔數據物件可能在另一個編輯器中打開,或者文檔數據可能已在具有相同編輯器的不同視圖中打開。 如果文件資料在編輯器工廠不支援的不同編輯器中打開,則 Visual Studio 無法打開編輯器工廠。 關於詳細資訊,請參閱[如何:將檢視附加到文件資料](../extensibility/how-to-attach-views-to-document-data.md)。
