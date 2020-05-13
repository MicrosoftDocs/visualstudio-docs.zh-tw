---
title: 儲存自訂文件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f04d588b4becfa778407269849032ea8ec56fb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705619"
---
# <a name="saving-a-custom-document"></a>儲存自訂文件
環境處理 **「儲存**」、**儲存為**「**儲存所有命令**」。 當使用者按下「**儲存**」、「**儲存為**」**或「全部儲存**」 到 **「檔案**」功能表或關閉解決方案,導致「全部儲存」時,將發生以下過程。

 ![客戶編輯器儲存](../../extensibility/internals/media/private.gif "Private")為自訂編輯器儲存、儲存為及儲存所有指令處理

 此過程在以下步驟中進行了詳細說明:

1. 對於 **"保存****和保存為"** 命令,<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>環境使用 服務來確定活動文檔視窗,從而確定哪些項應保存。 知道活動文件視窗后,環境在正在運行的文檔表中查找文檔的層次結構指標和項識別碼 (itemID)。 有關詳細資訊,請參閱[執行文件表](../../extensibility/internals/running-document-table.md)。

     對於"全部儲存"命令,環境使用正在運行的文檔表中的資訊編譯要儲存的所有項的清單。

2. 當解決方案收到呼叫時<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>,它會通過所選項集(<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>即服務公開的多個選擇)進行遍接。

3. 在所選內容中的每個項上,解決方案使用層次結構指標調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>方法來確定是否應啟用「保存功能表」 命令。 如果一個或多個項目髒,則啟用"保存"命令。 如果層次結構使用標準編輯器,則層次結構通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>方法將查詢臟狀態的層次結構委託給編輯器。

4. 在每個臟的選定項上,解決方案使用層次結構指標在適當的層次結構上調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>方法。

     對於自定義編輯器,文檔數據物件和專案之間的通信是私有的。 因此,在這兩個對象之間處理任何特殊的持久性問題。

    > [!NOTE]
    > 如果實現自己的持久性,請確保調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>方法以節省時間。 此方法檢查以確保保存檔是安全的(例如,該檔不是唯讀的)。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)
