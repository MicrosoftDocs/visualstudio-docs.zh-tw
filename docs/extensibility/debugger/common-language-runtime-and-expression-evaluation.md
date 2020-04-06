---
title: 通用語言執行時和運算中計算 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 013579473189dd9310501b76d2de0d5cf6fa5822
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739118"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>通用語言執行時與表示式運算
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 面向通用語言運行時 (CLR) 的編譯器(如 Visual Basic 和 C#(發音為 C-sharp))生成 Microsoft 中間語言 (MSIL),後者後來被編譯為本機代碼。 CLR 提供調試引擎 (DE) 來調試生成的代碼。 如果您計劃將專有程式設計語言整合到 Visual Studio IDE 中,您可以選擇編譯到 MSIL,因此不必編寫自己的 DE。 但是,您必須編寫一個表示式賦值器 (EE),該運算式評估器能夠評估程式設計語言上下文中的運算式。

## <a name="discussion"></a>討論區
 通常對計算機語言表達式進行分析以生成一組數據物件和一組用於操作它們的運算符。 例如,可以分析表達式「A+B」以將添加運算符 (+) 應用於數據物件「A」和「B」,這可能導致另一個數據物件。 數據物件、運算元及其關聯的總集通常以樹的形式在程式中表示,其中運算符位於樹的節點處,數據物件位於分支。 分解為樹形的表達式通常稱為解析樹。

 分析表示式後,將調用符號提供程式 (SP) 以評估每個數據物件。 例如,如果「A」在多種方法中同時定義,則問題「哪個 A? 必須先回答,然後才能確定 A 的值。 SP 返回的答案類似於"第五堆棧幀上的第三項"或"A 是 50 位元組,超出分配給此方法的靜態記憶體的開頭。

 除了為程式本身生成 MSIL 外,CLR 編譯器還可以生成非常描述性的調試資訊,這些資訊寫入程式資料庫 *(.pdb*) 檔中。 只要專有語言編譯器生成與 CLR 編譯器相同的格式的調試資訊,CLR 的 SP 就能標識該語言的命名數據物件。 標識命名數據物件後,EE 使用活頁夾物件將數據物件關聯(或綁定)到保存該物件值的記憶體區域。 然後,DE 可以獲取或設置數據物件的新值。

 專有編譯器可以通過調`ISymbolWriter`用 介面(在`System.Diagnostics.SymbolStore`命名空間 中的 .NET 框架中定義)來提供 CLR 調試資訊。 通過編譯到 MSIL 並透過這些介面編寫除錯資訊,專有編譯器可以使用 CLR DE 和 SP。 這大大簡化了將專有語言集成到可視化工作室 IDE 中。

 當 CLR DE 調用專有 EE 以評估運算式時,DE 向 EE 提供 SP 和活頁夾物件的介面。 因此,編寫基於 CLR 的調試引擎意味著只需實現適當的運算式賦值器介面;CLR 負責綁定和符號處理。

## <a name="see-also"></a>另請參閱
- [編寫 CLR 表示式賦值器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
