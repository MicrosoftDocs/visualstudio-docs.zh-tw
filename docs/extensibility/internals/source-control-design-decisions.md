---
title: 原始檔控制設計決策 |Microsoft Docs
description: 瞭解在執行原始檔控制時，針對專案考慮的幾個重要設計決策。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 82afa3bfee446ab5bd214fd5ac58dbfac9523467
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069318"
---
# <a name="source-control-design-decisions"></a>原始檔控制的設計決策
執行原始檔控制時，應考慮專案的下列設計決策。

## <a name="will-information-be-shared-or-private"></a>資訊是共用或私用的？
 您可以進行的最重要設計決策是可共用的資訊，以及私用的資訊。 例如，專案的檔案清單是共用的，但在這份檔案清單中，某些使用者可能會想要有私用檔案。 編譯器設定是共用的，但啟動專案通常是私用的。 設定可以純粹共用、與覆寫共用，或純粹是私用。 根據設計，不會簽入私用專案，例如方案使用者選項 ( .suo) 檔 [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] 。 請務必將任何私用資訊儲存在私用檔案（例如 .suo 檔案）或您建立的特定私用檔案（例如，適用于 Visual c # 的 .csproj. 使用者檔案或 vbproj）中，以進行 Visual Basic。

 這項決定並非全部包含，而且可以依專案逐一進行。

## <a name="will-the-project-include-special-files"></a>專案會包含特殊檔案嗎？
 另一個重要的設計決策是您的專案結構是否使用特殊檔案。 特殊檔案是隱藏的檔案，其構成方案總管以及簽入和簽出對話方塊中顯示的檔案。 如果您使用特殊檔案，請遵循下列指導方針：

1. 請勿將特殊檔案與專案根節點建立關聯，也就是專案檔本身。 您的專案檔必須是單一檔案。

2. 在專案中加入、移除或重新命名特殊檔案時， <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> 必須使用指出檔案為特殊檔案的旗標設定來引發適當的事件。 這些事件會由環境呼叫，以回應呼叫適當方法的專案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 。

3. 當您的專案或編輯器呼叫檔案時 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ，不會自動簽出與該檔案相關聯的特殊檔案。將特殊檔案連同父檔案一起傳遞。 環境會偵測傳入的所有檔案之間的關聯性，並適當地隱藏簽出 UI 中的特殊檔案。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)
