---
title: 儲存標準文件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8d50a9e62e69f925564717020a51f88620f5f3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705543"
---
# <a name="saving-a-standard-document"></a>儲存標準文件
環境處理「保存、保存為」和「儲存所有」命令。 當使用者選擇 **「保存**」、「**儲存為**」或從 **「檔案」** 選單中**儲存全部**內容或關閉解決方案,從而導致 **「全部儲存**」時,將發生以下過程。

 ![標準編輯器](../../extensibility/internals/media/public.gif "公開")為標準編輯器儲存、儲存為與儲存所有指令處理

 此過程在以下步驟中進行了詳細說明:

1. 選擇 **"保存****和保存為"** 命令時,環境<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>將使用 該服務來確定活動文檔視窗,從而確定應儲存哪些項。 知道活動文件視窗后,環境在正在運行的文檔表中查找文檔的層次結構指標和項識別碼 (itemID)。 有關詳細資訊,請參閱[執行文件表](../../extensibility/internals/running-document-table.md)。

    選擇「**全部儲存」** 指令後,環境將使用正在執行的文件表中的資訊編譯要儲存的所有項的清單。

2. 當解決方案收到呼叫時<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>,它會通過所選項集(<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>即服務公開的多個選擇)進行遍接。

3. 在所選內容中的每個項上,解決方案使用層次結構指標調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>方法來確定是否應啟用 **「保存**功能表」。 如果一個或多個項目髒,則啟用 **"保存**"命令。 如果層次結構使用標準編輯器,則層次結構通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>方法將查詢臟狀態的層次結構委託給編輯器。

4. 在每個臟的選定項上,解決方案使用層次結構指標在適當的層次結構上調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>方法。

    層次結構通常使用標準編輯器編輯文檔。 在這種情況下,該編輯器的文檔數據物件應支援<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>該介面。 收到<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>方法調用後,專案應通過在文檔數據物件上調<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A>用 方法來通知編輯器文檔正在保存。 編輯器可以通過調`Query Service`<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>用 介面來允許環境處理 **「另存即」** 對話方塊。 這將返回指向介面的<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>指標。 然後,編輯器必須調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>方法,<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>`pPersistFile`通過 參數傳遞指向編輯器實現的指標。 然後,環境執行"保存"操作,並為編輯器提供 **「另存為**」對話方塊。 然後,環境使用<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>調用回編輯器。

5. 如果使用者嘗試保存無標題文檔(即以前未儲存的文檔),則實際執行"保存為"命令。

6. 對於"保存為"命令,環境將顯示"另存為"對話框,提示使用者輸入檔名。

    如果檔的名稱已更改,則層次結構負責通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument)更新文檔幀的緩存資訊。

   如果 **「保存為」** 命令移動文件的位置,並且層次結構對文檔位置很敏感,則層次結構負責將打開的文檔視窗的擁有權移交給其他層次結構。 例如,如果專案跟蹤檔是與專案相關的內部檔還是外部檔(雜項檔),則會發生這種情況。 使用以下過程將檔的擁有權更改為「雜項檔」 專案。

## <a name="changing-file-ownership"></a>變更檔案擁有權

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>將檔案擁有權變更為「雜項檔」 專案

1. 查詢介面的服務<xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>。

     返回指向<xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2>的指標。

2. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A>`pszMkDocumentNew` `punkWindowFrame`( ) 方法以將文件傳輸到新層次結構。 執行「保存為」命令的層次結構調用此方法。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)
