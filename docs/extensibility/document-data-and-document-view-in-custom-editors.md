---
title: 自訂編輯器中的文件資料和文件檢視 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04e89194ff09bc273294246cc25718c999daf70f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712138"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>自訂編輯器中的文件資料與文件檢視
自定義編輯器由兩部分組成:文件數據對象和文檔檢視物件。 如名稱建議,文檔數據物件表示要顯示的文本數據。 同樣,文件檢視物件(或"視圖")表示一個或多個視窗,其中用於顯示文檔數據物件。

## <a name="document-data-object"></a>文件資料物件
 文件資料物件是文本緩衝區中文本的數據表示形式。 它是儲存文件文本和其他資訊的 COM 物件。 文件數據物件還處理文檔持久性,並啟用其資料的多個檢視。 如需相關資訊，請參閱

 <xref:EnvDTE80.Window2.DocumentData%2A>與[文件視窗](../extensibility/internals/document-windows.md)。

 自定義編輯器和設計器可以選擇使用<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>對象或他們自己的自定義緩衝區。 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>遵循標準編輯器的簡化嵌入模型,支援多個檢視,並提供用於管理多個視圖的事件介面。

## <a name="document-view-object"></a>文件檢視物件
 顯示代碼和其他文本的窗口稱為文檔檢視或檢視。 創建編輯器時,可以選擇單個檢視,其中文本顯示在單個視窗中。 或者,您可以選擇多個檢視,其中文本顯示在多個視窗中。 您的選擇取決於您的應用程式。 例如,如果需要並行編輯,請選擇多個檢視。 每個檢視都與整合式開發環境 (IDE) 執行的文件表 (RDT) 中的條目相關聯。 視圖窗口屬於專案或<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>物件。

 如果編輯器支援文檔數據物件的多個檢視,則文檔數據和文檔檢視物件必須分開。 否則,它們可以分組在一起。 有關詳細資訊,請參閱[支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)。

 IDE 透過匹配正在執行的文件表中每個條目的項識別碼 (ItemID)來通知有關事件的檢視(例如,當包含文件的解決方案關閉時)。 有關此的詳細資訊,請參閱[執行文件表](../extensibility/internals/running-document-table.md)。

 有兩個選項用於為自訂編輯器創建檢視。 一個是就地啟動模型,其中檢視使用 ActiveX 控制件或文檔數據物件託管在視窗中。 第二個是簡化的嵌入模型,其中視圖由[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]該模型託管,並<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>實現以處理視窗命令。 有關就地啟動模型的資訊,請參閱[就地啟動](/visualstudio/misc/in-place-activation?view=vs-2015)。 有關簡化嵌入模型的資訊,請參閱[簡化嵌入](../extensibility/simplified-embedding.md)。

## <a name="see-also"></a>另請參閱

- [支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)
- [簡化的嵌入](../extensibility/simplified-embedding.md)
- [如何:將檢視附加到文件資料](../extensibility/how-to-attach-views-to-document-data.md)
- [文件鎖定者管理](../extensibility/document-lock-holder-management.md)
- [單選項卡與多選項卡檢視](../extensibility/single-and-multi-tab-views.md)
- [儲存標準文件](../extensibility/internals/saving-a-standard-document.md)
- [持久性和正在執行的文件表](../extensibility/internals/persistence-and-the-running-document-table.md)
- [確定哪個編輯器開啟檔案](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)
