---
title: 源代碼管理設定詳細資訊 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cf4a5c55e8093e5dcd6406cde1c60f642188495
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705287"
---
# <a name="source-control-configuration-details"></a>原始檔控制組態的詳細資料
為了實現原始碼管理,您需要正確設定專案系統或編輯器,以便執行以下操作:

- 要求將轉換到已變更狀態的權限

- 要求儲存檔案的權限

- 要求在項目中新增、刪除或重新命名檔案的權限

## <a name="request-permission-to-transition-to-changed-state"></a>要求轉換到變更狀態的權限
 專案或編輯器必須透過呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>請求請求轉換為已更改的(髒)狀態。 設定<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>的每個編輯器都必須呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>並收到批准才能從環境中更改文件,然後才能`True`返回<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>。 專案本質上是專案檔的編輯器,因此,與文本編輯器對其檔執行更改狀態跟蹤具有相同的責任。 環境處理解決方案的更改狀態,但必須處理解決方案引用但不儲存的任何物件的更改狀態,如專案檔或其項。 通常,如果專案或編輯器負責管理專案的持久性,則負責實現更改狀態跟蹤。

 為了回應呼叫,`IVsQueryEditQuerySave2::QueryEditFiles`環境可以執行以下操作:

- 拒絕更改呼叫,在這種情況下,編輯器或項目必須保持未更改(乾淨)狀態。

- 指示應重新載入文件數據。 對於專案,環境將重新載入項目的數據。 編輯器必須透過磁碟<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>實現重新載入資料。 在這兩種情況下,專案或編輯器中的上下文都可以在重新載入數據時更改。

  將適當的`IVsQueryEditQuerySave2::QueryEditFiles`調用改裝到現有代碼庫是一項複雜而艱巨的任務。 因此,應在創建專案或編輯器期間集成這些調用。

## <a name="request-permission-to-save-a-file"></a>要求儲存檔案的權限
 在項目或編輯器儲存檔之前,它必須呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>。 對於專案檔,這些調用由解決方案自動完成,解決方案知道何時保存專案檔。 編輯器負責進行這些調用,除非編輯器實現`IVsPersistDocData2`使用説明器函數<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>。 如果編輯器以這種方式實現`IVsPersistDocData2`,則呼`IVsQueryEditQuerySave2::QuerySaveFile`叫`IVsQueryEditQuerySave2::QuerySaveFiles`或為您進行呼叫。

> [!NOTE]
> 始終先發制人地撥打這些呼叫,即,在編輯能夠收到取消時。

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>要求在項目中新增、刪除或重新命名檔案的權限
 在專案可以添加、重新命名或刪除檔案或目錄之前,它必須調用適當的`IVsTrackProjectDocuments2::OnQuery*`方法來請求環境的許可權。 如果授予許可權,則專案必須完成該操作,然後調用適當的`IVsTrackProjectDocuments2::OnAfter*`方法來通知環境操作已完成。 項目必須調用所有檔的<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>介面方法(例如,特殊檔),而不僅僅是父檔。 檔調用是必填項,但目錄調用是可選的。 如果專案具有目錄資訊,則應調用適當的<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>方法,但如果它沒有此資訊,則環境將推斷目錄資訊。

 專案不應調用 項目打開或`IVsTrackProjectDocuments2`關閉 時的方法。 在啟動時想要此資訊的偵聽器可以等待<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>事件並遍遍解決方案以查找所需的資訊。 關閉時,不需要此資訊。 `IVsTrackProjectDocuments2`從提供<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>。

 對於每個添加、重新命名和刪除操作,都有一個`OnQuery*`方法和一個`OnAfter*`方法。 呼叫`OnQuery*`方法以請求添加、重新命名或刪除檔案或目錄的許可權。 在`OnAfter*`添加、重新命名或刪除檔案或目錄並刪除項目狀態後調用方法,並反映新狀態。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)
