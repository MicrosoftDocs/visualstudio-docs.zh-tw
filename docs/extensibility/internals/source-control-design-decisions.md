---
title: 源代碼管理設計決策 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c36bb2b50a72a52aeaeb7712f4ed711845b5e6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705250"
---
# <a name="source-control-design-decisions"></a>原始檔控制的設計決策
在實現原始程式碼管理時,應考慮以下設計決策。

## <a name="will-information-be-shared-or-private"></a>信息是共享還是私有?
 您可以做出的最重要的設計決策是哪些資訊是可共用的,什麼是私有的。 例如,專案的檔案清單是共用的,但在此檔案清單中,某些使用者可能希望具有私有檔。 編譯器設置是共用的,但啟動專案通常是私有的。 設置是純共用的、與重寫共用的,或者純粹是私有的。 根據設計,私有專案(如解決方案使用者選項 (.suo) 檔案)不會[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]簽入 。 請務必將任何私有資訊儲存在私有檔(如 .suo 檔)或您創建的特定私有檔(例如,Visual C# 的 .csproj.user 檔案)或 Visual Basic 的 .vbproj.user 檔中。

 此決定並非包羅萬象,可以逐項做出。

## <a name="will-the-project-include-special-files"></a>該專案將包括特殊檔嗎?
 另一個重要的設計決策是專案結構是否使用特殊檔。 特殊檔案是隱藏檔案,這些檔案是解決方案資源管理員和簽入和簽出對話框中可見的檔案的隱藏檔。 如果您使用特殊檔案,請遵循以下準則:

1. 不要將特殊文件與專案根節點(即專案檔本身)相關聯。 項目檔必須是單個檔。

2. 在專案中添加、刪除或重命名特殊檔時,必須使用指示檔為特殊<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>檔案的標誌集觸發相應的事件。 這些事件由環境調用,以回應調用相應<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>方法的專案。

3. 當專案或編輯器呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>檔案時,與該文件關聯的特殊檔不會自動簽出。將特殊檔與父檔一起傳遞。 環境將檢測傳入的所有文件之間的關係,並適當隱藏簽出 UI 中的特殊檔。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)
