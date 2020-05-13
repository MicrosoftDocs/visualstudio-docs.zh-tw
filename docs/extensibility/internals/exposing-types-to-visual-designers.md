---
title: 向視覺設計器公開類型 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9067f88b4bf1334e23a548bc6a2cbeb3eac6ad33
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708429"
---
# <a name="expose-types-to-visual-designers"></a>以視覺化設計器公開類型
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]必須在設計時存取類和類型定義才能顯示可視化設計器。 類從預定義的程式集集載入,其中包括當前專案的完整依賴項集(引用及其依賴項)。 可視化設計人員可能還需要訪問在自定義工具生成的檔中定義的類和類型。

 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]和[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]專案系統支援透過暫時可移植可執行檔(臨時 P)存取生成的類和類型。 自定義工具生成的任何檔都可以編譯到臨時程式集中,以便可以從這些程式集載入類型並公開給設計人員。 每個自定義工具的輸出都編譯成單獨的臨時 PE,此臨時編譯的成敗僅取決於是否可以編譯生成的檔。 即使專案可能無法作為一個整體進行構建,但各個臨時 P 可能仍可供設計人員使用。

 專案系統完全支援追蹤對自定義工具的輸出檔的更改,前提是這些更改是運行自定義工具的結果。 每次運行自定義工具時,都會生成新的臨時 PE,並將適當的通知發送給設計人員。

> [!NOTE]
> 由於臨時程式可執行生成檔發生在後台,因此在編譯失敗時不會向用戶報告任何錯誤。

 利用暫時的「自訂」工具必須遵循以下規則:

- **生成設計時間源**必須在註冊表中設置為 1。

     沒有此設置,則不執行任何程式可執行檔編譯。

- 生成的代碼必須與全域項目設置的語言相同。

     無論自定義工具在註冊表中<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>設置為 1 時,無論自定義工具作為請求**GeneratesDesignTimeSource**的擴展報告 什麼,都會編譯臨時 PE。 擴展不需要是 *.vb、.cs**.cs*或 *.jsl;* 它可以是任何擴展。

- 自定義工具生成的代碼必須有效,並且必須僅使用執行完時<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>專案中存在的引用集自行編譯。

     編譯暫時 PE 時,提供給編譯器的唯一源檔是自定義工具輸出。 因此,使用臨時 PE 的自定義工具必須生成可獨立於專案中其他檔編譯的輸出檔。

## <a name="see-also"></a>另請參閱
- [BuildManager 物件的簡介](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
- [實現單檔產生器](../../extensibility/internals/implementing-single-file-generators.md)
- [註冊單檔產生器](../../extensibility/internals/registering-single-file-generators.md)
