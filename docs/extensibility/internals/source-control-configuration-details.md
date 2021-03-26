---
title: 原始檔控制設定詳細資料 |Microsoft Docs
description: 瞭解如何在 Visual Studio 中執行專案類型的原始檔控制，其中牽涉到設定您的專案系統或編輯器來要求許可權。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a5c93e690922057116b395bed3881627e8a37847
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069344"
---
# <a name="source-control-configuration-details"></a>原始檔控制組態的詳細資料
若要執行原始檔控制，您需要適當地設定您的專案系統或編輯器，以執行下列動作：

- 要求轉換為變更狀態的許可權

- 要求儲存檔案的許可權

- 在專案中加入、移除或重新命名檔案的要求許可權

## <a name="request-permission-to-transition-to-changed-state"></a>要求轉換為變更狀態的許可權
 專案或編輯器必須藉由呼叫來要求轉換為變更的 (變更) 狀態的許可權 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> 。 每個執行的編輯器都 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> 必須呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 並接收核准，才能在傳回之前，從環境變更檔 `True` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> 。 專案基本上是專案檔的編輯器，如此一來，就會有相同的責任，可針對專案檔執行變更狀態追蹤，做為其檔案的文字編輯器。 環境會處理解決方案的變更狀態，但您必須處理方案所參考但未儲存之任何物件的變更狀態，例如專案檔或其專案。 一般而言，如果您的專案或編輯器負責管理專案的持續性，則會負責執行變更狀態追蹤。

 為了回應 `IVsQueryEditQuerySave2::QueryEditFiles` 呼叫，環境可以執行下列作業：

- 拒絕要變更的呼叫，在這種情況下，編輯器或專案必須保持不變 (乾淨) 狀態。

- 指出應重載檔資料。 若為專案，環境將會重載專案的資料。 編輯器必須透過其執行從磁片重載資料 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> 。 在任何一種情況下，專案或編輯器中的內容都可以在重載資料時變更。

  在 `IVsQueryEditQuerySave2::QueryEditFiles` 現有的程式碼基底上改建適當的呼叫，是一項複雜且困難的工作。 如此一來，在專案或編輯器建立期間，這些呼叫應該會整合。

## <a name="request-permission-to-save-a-file"></a>要求儲存檔案的許可權
 在專案或編輯器儲存檔案之前，它必須呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> 。 若為專案檔，方案會自動完成這些呼叫，這會知道何時要儲存專案檔。 除非的編輯器執行使用 helper 函式，否則編輯器會負責進行這些呼叫 `IVsPersistDocData2` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> 。 如果您的編輯器 `IVsPersistDocData2` 是以這種方式進行，則 `IVsQueryEditQuerySave2::QuerySaveFile` `IVsQueryEditQuerySave2::QuerySaveFiles` 會為您進行或的呼叫。

> [!NOTE]
> 一律讓這些呼叫事先，也就是當您的編輯器能夠接收取消時。

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>在專案中加入、移除或重新命名檔案的要求許可權
 在專案可以新增、重新命名或移除檔案或目錄之前，必須先呼叫適當的 `IVsTrackProjectDocuments2::OnQuery*` 方法來要求環境的許可權。 如果授與許可權，則專案必須完成作業，然後呼叫適當的方法， `IVsTrackProjectDocuments2::OnAfter*` 以通知環境作業已完成。 專案必須呼叫所有檔案的介面方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> (例如，特殊檔案) ，而不只是父檔案。 檔案呼叫是必要的，但目錄呼叫是選擇性的。 如果您的專案有目錄資訊，則應呼叫適當的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 方法，但如果沒有此資訊，則環境會推斷目錄資訊。

 專案不應該 `IVsTrackProjectDocuments2` 在專案開啟或關閉時呼叫的方法。 在啟動時需要這項資訊的接聽程式可以等候 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> 事件，並逐一查看解決方案以找出所需的資訊。 關機時，不需要這項資訊。 `IVsTrackProjectDocuments2` 是由提供的 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> 。

 針對每個新增、重新命名和移除動作，都有 `OnQuery*` 方法和 `OnAfter*` 方法。 呼叫 `OnQuery*` 方法，以要求新增、重新命名或移除檔案或目錄的許可權。 在 `OnAfter*` 新增、重新命名或移除檔案或目錄之後，以及專案狀態反映新狀態之後，呼叫方法。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)
