---
title: 原始檔控制設定詳細資料 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a6c51dfe4ad9378af04da61dbd7e9011c4678f1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723800"
---
# <a name="source-control-configuration-details"></a>原始檔控制組態的詳細資料
若要執行原始檔控制，您必須適當地設定您的專案系統或編輯器，以執行下列動作：

- 要求轉換至已變更狀態的許可權

- 要求儲存檔案的許可權

- 要求在專案中新增、移除或重新命名檔案的許可權

## <a name="request-permission-to-transition-to-changed-state"></a>要求轉換至已變更狀態的許可權
 專案或編輯器必須藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>，要求轉換至已變更（中途）狀態的許可權。 每個執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> 的編輯器都必須呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 並接受核准，才能在傳回 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> 的 `True` 之前，從環境中變更檔。 專案基本上是專案檔的編輯器，因此，針對專案檔執行變更狀態追蹤的責任，就如同文字編輯器對其檔案所做的一樣。 環境會處理解決方案的已變更狀態，但是您必須處理解決方案所參考但不會儲存之任何物件的已變更狀態，例如專案檔或其專案。 一般來說，如果您的專案或編輯器負責管理專案的持續性，則它會負責執行變更狀態追蹤。

 為了回應 `IVsQueryEditQuerySave2::QueryEditFiles` 呼叫，環境可以執行下列動作：

- 拒絕變更的呼叫，在此情況下，編輯器或專案必須維持不變（清除）狀態。

- 指出應該重載檔資料。 針對專案，環境會重載專案的資料。 編輯器必須透過其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> 的執行，從磁片重載資料。 不論是哪一種情況，當重載資料時，專案或編輯器中的內容都可以變更。

  將適當的 `IVsQueryEditQuerySave2::QueryEditFiles` 呼叫)) 到現有的程式碼基底，是一項複雜且艱難的工作。 因此，這些呼叫應該在專案或編輯器建立期間進行整合。

## <a name="request-permission-to-save-a-file"></a>要求儲存檔案的許可權
 在專案或編輯器儲存檔案之前，它必須先呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>。 針對專案檔，解決方案會自動完成這些呼叫，這會知道儲存專案檔的時機。 除非 `IVsPersistDocData2` 的編輯器實作用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> 的 helper 函式，否則編輯器會負責進行這些呼叫。 如果您的編輯器以這種方式執行 `IVsPersistDocData2`，則會為您進行 `IVsQueryEditQuerySave2::QuerySaveFile` 或 `IVsQueryEditQuerySave2::QuerySaveFiles` 的呼叫。

> [!NOTE]
> 請一律讓這些呼叫事先，也就是您的編輯器可以接收取消的時間。

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>要求在專案中新增、移除或重新命名檔案的許可權
 在專案可以新增、重新命名或移除檔案或目錄之前，它必須呼叫適當的 `IVsTrackProjectDocuments2::OnQuery*` 方法，以要求環境的許可權。 如果授與許可權，則專案必須完成作業，然後呼叫適當的 `IVsTrackProjectDocuments2::OnAfter*` 方法，以通知環境作業已完成。 專案必須為所有檔案（例如，特殊檔案）呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 介面的方法，而不只是父檔案。 檔案呼叫是必要的，但目錄呼叫是選擇性的。 如果您的專案有目錄資訊，則它應該呼叫適當的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 方法，但如果沒有此資訊，則環境會推斷目錄資訊。

 專案不應在專案開啟或關閉時呼叫 `IVsTrackProjectDocuments2` 的方法。 在啟動時需要這項資訊的接聽程式可以等候 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> 事件，並逐一查看解決方案來尋找所需的資訊。 關閉時，不需要此資訊。 `IVsTrackProjectDocuments2` 是從 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> 提供。

 針對每個 [新增]、[重新命名] 和 [移除] 動作，有一個 `OnQuery*` 方法和一個 `OnAfter*` 方法。 呼叫 `OnQuery*` 方法，以要求新增、重新命名或移除檔案或目錄的許可權。 在新增、重新命名或移除檔案或目錄之後，以及專案狀態反映新狀態之後，呼叫 `OnAfter*` 方法。

## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)