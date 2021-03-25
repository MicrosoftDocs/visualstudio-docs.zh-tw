---
title: 將類型公開至視覺化設計工具 |Microsoft Docs
description: 瞭解如何公開類別和類型定義（包括自訂工具中的定義），以便 Visual Studio 可提供給視覺化設計工具。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5208de3af52e4dad5fb9bb59b16f7b59efb72340
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069669"
---
# <a name="expose-types-to-visual-designers"></a>將類型公開至視覺化設計工具
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 必須能夠在設計階段存取類別和類型定義，才能顯示視覺化設計工具。 類別是從一組預先定義的元件載入，其中包含目前專案的完整相依性集合， (參考加上) 的相依性。 視覺化設計工具也可能需要存取自訂工具所產生的檔案中所定義的類別和類型。

 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]和 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 專案系統透過暫存的可執行檔 (暫時性的 pe) ，支援存取產生的類別和類型。 自訂工具產生的任何檔案都可以編譯成暫存元件，以便從這些元件載入型別並公開給設計工具。 每個自訂工具的輸出會編譯成個別的暫存 PE，而此暫存編譯的成功或失敗只取決於是否可以編譯產生的檔案。 雖然專案可能無法整體建立，但是個別的暫存 Pe 可能仍可供設計人員使用。

 專案系統提供完整的支援，可追蹤自訂工具輸出檔的變更，但前提是這些變更是執行自訂工具的結果。 每次執行自訂工具時，都會產生新的暫存 PE，並將適當的通知傳送至設計工具。

> [!NOTE]
> 因為暫時性程式可執行檔產生檔會在背景中執行，所以如果編譯失敗，就不會向使用者回報錯誤。

 利用暫時性 PE 支援的自訂工具必須遵循下列規則：

- **GeneratesDesignTimeSource** 在登錄中必須設定為1。

     沒有此設定，就不會進行程式可執行檔編譯。

- 產生的程式碼必須與全域專案設定的語言相同。

     無論自訂工具在登錄中的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> **GeneratesDesignTimeSource** 設定為1，都將會編譯暫存的 PE，無論自訂工具會將它報告為所要求的擴充功能。 延伸模組不需要是 *.vb*、 *.cs* 或 *. form1.jsl*;它可以是任何延伸模組。

- 自訂工具產生的程式碼必須是有效的，而且它必須只使用在執行完成時存在於專案中的一組參考來進行編譯 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> 。

     編譯暫存 PE 時，唯一提供給編譯器的原始程式檔是自訂工具輸出。 因此，使用暫存 PE 的自訂工具必須產生輸出檔案，而這些輸出檔案可以獨立于專案中的其他檔案進行編譯。

## <a name="see-also"></a>另請參閱
- [BuildManager 物件簡介](/previous-versions/8f9kffa8(v=vs.140))
- [執行單一檔案產生器](../../extensibility/internals/implementing-single-file-generators.md)
- [註冊單一檔案產生器](../../extensibility/internals/registering-single-file-generators.md)