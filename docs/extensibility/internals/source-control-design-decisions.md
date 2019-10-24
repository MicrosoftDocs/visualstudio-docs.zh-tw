---
title: 原始檔控制設計決策 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a7c8a902520323f548a7dd77a84b07a56bfc9a0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723607"
---
# <a name="source-control-design-decisions"></a>原始檔控制的設計決策
在執行原始檔控制時，應該考慮下列設計決策的專案。

## <a name="will-information-be-shared-or-private"></a>資訊會是共用或私用？
 您可以做的最重要設計決策是可共用的資訊，以及私用的內容。 例如，專案的檔案清單是共用的，但在此檔案清單中，某些使用者可能會想要有私用檔案。 編譯器設定是共用的，但是啟動專案通常是私用的。 設定是單純共用、與覆寫共用，或純粹是私用。 根據設計，私用專案（例如解決方案使用者選項（.suo）檔案）不會簽入 [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]。 請務必將任何私用資訊儲存在私用檔案中，例如 .suo 檔案，或您建立的特定私用檔案（例如，用於視覺效果C#的 .csproj. 使用者檔案），或 vbproj 使用者檔案以進行 Visual Basic。

 這項決定並非全部都包含，而且可以依專案逐一進行。

## <a name="will-the-project-include-special-files"></a>專案是否會包含特殊檔案？
 另一個重要的設計決策是您的專案結構是否使用特殊檔案。 特殊檔案是隱藏的檔案，其基礎是在方案總管中顯示的檔案，以及在 [簽入] 和 [簽出] 對話方塊中的檔。 如果您使用特殊檔案，請遵循下列指導方針：

1. 請勿將特殊檔案與專案根節點（也就是專案檔本身）產生關聯。 您的專案檔必須是單一檔案。

2. 在專案中新增、移除或重新命名特殊檔案時，必須使用指出檔案是特殊檔案的旗標設定來引發適當的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> 事件。 這些事件是由環境呼叫，以回應呼叫適當 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 方法的專案。

3. 當您的專案或編輯器呼叫檔案的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 時，與該檔案相關聯的特殊檔案不會自動簽出。連同父檔案一起傳遞中的特殊檔案。 環境會偵測傳入的所有檔案之間的關聯性，並在簽出 UI 中適當地隱藏特殊檔案。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)