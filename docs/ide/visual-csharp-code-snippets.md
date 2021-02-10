---
title: C# 程式碼片段
description: '瞭解如何使用程式碼片段將常用的程式碼新增至 c # 程式碼檔案。'
ms.custom: SEO-VS-2020
ms.date: 06/05/2017
ms.topic: reference
helpviewer_keywords:
- snippets [C#]
- code snippets [C#]
- Code Snippet Inserter [C#]
- C#, code snippets
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e4656e0769075be26db5bd06108093a49fb5e2af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941537"
---
# <a name="c-code-snippets"></a>C# 程式碼片段

程式碼片段是可快速插入程式碼的現成程式碼片段。 例如，`for` 程式碼片段會建立空白 `for` 迴圈。 部分程式碼片段是範圍陳述式程式碼片段，可讓您選取程式碼行，然後選擇包含所選取程式碼行的程式碼片段。 例如，如果您選取程式碼行，然後啟用 `for` 程式碼片段，則會建立迴圈區塊內包含這些程式碼行的 `for` 迴圈。 程式碼片段可以更快速、更輕鬆且更可靠地撰寫程式碼。

您可以在游標位置插入程式碼片段，或在目前選取的程式碼周圍插入範圍陳述式程式碼片段。 程式碼片段插入器的叫用方式是透過 **IntelliSense** 功能表上的 [插入程式碼片段] 或 [範圍陳述式] 命令，或分別依序使用鍵盤快速鍵 **Ctrl**+**K** 和 **X** 或 **Ctrl**+**K** 和 **S**。

**程式碼片段插入** 器會顯示所有可用程式碼片段的程式碼片段名稱。 程式碼片段插入器也會包含輸入對話方塊，您可以在其中輸入程式碼片段名稱或程式碼片段名稱的一部分。 程式碼片段插入器會反白顯示最接近程式碼片段名稱的相符項目。 隨時按下 **Tab 鍵** 將會關閉程式碼片段插入器，並插入目前選取的程式碼片段。 在程式碼編輯器中按 **ESC** 或按一下滑鼠會關閉程式碼片段插入器，而不插入程式碼片段。

## <a name="default-code-snippets"></a>預設程式碼片段

Visual Studio for C# 中預設會包含下列程式碼片段。

|名稱 (或捷徑)|Description|插入程式碼片段的有效位置|
| - |-----------------| - |
|#if|建立 [#if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) 指示詞和 [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif) 指示詞。|任何位置。|
|#region|建立 [#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) 指示詞和 [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion) 指示詞。|任何位置。|
|~|建立包含類別的[完成項](/dotnet/csharp/programming-guide/classes-and-structs/destructors) (解構函式)。|在類別內部。|
|屬性|建立衍生自 <xref:System.Attribute> 之類別的宣告。|在命名空間 (包含全域命名空間)、類別或結構內部。|
|checked|建立 [checked](/dotnet/csharp/language-reference/keywords/checked) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|Class - 類別|建立類別宣告。|在命名空間 (包含全域命名空間)、類別或結構內部。|
|ctor|建立包含類別的建構函式。|在類別內部。|
|cw|建立 <xref:System.Console.WriteLine%2A> 呼叫。|在方法、索引子、屬性存取子或事件存取子內。|
|do|建立 [do](/dotnet/csharp/language-reference/keywords/do) `while` 迴圈。|在方法、索引子、屬性存取子或事件存取子內。|
|else|建立 [else](/dotnet/csharp/language-reference/keywords/if-else) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|列舉|建立 [enum](/dotnet/csharp/language-reference/keywords/enum) 宣告。|在命名空間 (包含全域命名空間)、類別或結構內部。|
|equals|建立覆寫 <xref:System.Object> 類別中所定義 <xref:System.Object.Equals%2A> 方法的方法宣告。|在類別或結構內部。|
|exception|建立衍生自例外狀況之類別的宣告 (預設為 <xref:System.Exception>)。|在命名空間 (包含全域命名空間)、類別或結構內部。|
|對象|建立 [for](/dotnet/csharp/language-reference/keywords/for) 迴圈。|在方法、索引子、屬性存取子或事件存取子內。|
|foreach|建立 [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 迴圈。|在方法、索引子、屬性存取子或事件存取子內。|
|forr|建立在每個重複項目後遞減迴圈變數的 [for](/dotnet/csharp/language-reference/keywords/for) 迴圈。|在方法、索引子、屬性存取子或事件存取子內。|
|if|建立 [if](/dotnet/csharp/language-reference/keywords/if-else) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|索引子|建立索引子宣告。|在類別或結構內部。|
|介面|建立 [interface](/dotnet/csharp/language-reference/keywords/interface) 宣告。|在命名空間 (包含全域命名空間)、類別或結構內部。|
|叫用|建立安全地叫用事件的區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|迭代器|建立迭代器。|在類別或結構內部。|
|iterindex|使用巢狀類別建立 "named" 迭代器和索引子組。|在類別或結構內部。|
|鎖定|建立 [lock](/dotnet/csharp/language-reference/keywords/lock-statement) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|mbox|建立 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> 呼叫。 您可能必須新增 *System.Windows.Forms.dll* 的參考。|在方法、索引子、屬性存取子或事件存取子內。|
|命名空間|建立 [namespace](/dotnet/csharp/language-reference/keywords/namespace) 宣告。|在命名空間 (包含全域命名空間) 內部。|
|prop|建立[自動實作的屬性](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties)宣告。|在類別或結構內部。|
|propfull|建立具有 `get` 和 `set` 存取子的屬性宣告。|在類別或結構內部。|
|propg|建立具有私用 `set` 存取子的唯讀[自動實作的屬性](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties)。|在類別或結構內部。|
|sim|建立 [static](/dotnet/csharp/language-reference/keywords/static) [int](/dotnet/csharp/language-reference/keywords/int) Main 方法宣告。|在類別或結構內部。|
|struct|建立 [struct](/dotnet/csharp/language-reference/keywords/struct) 宣告。|在命名空間 (包含全域命名空間)、類別或結構內部。|
|svm|建立 [static](/dotnet/csharp/language-reference/keywords/static) [void](/dotnet/csharp/language-reference/keywords/void) Main 方法宣告。|在類別或結構內部。|
|switch|建立 [switch](/dotnet/csharp/language-reference/keywords/switch) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|嘗試|建立 [try-catch](/dotnet/csharp/language-reference/keywords/try-catch) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|tryf|建立 [try-finally](/dotnet/csharp/language-reference/keywords/try-finally) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|unchecked|建立 [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|unsafe|建立 [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|using|建立 [using](/dotnet/csharp/language-reference/keywords/using-directive) 指示詞。|在命名空間 (包含全域命名空間) 內部。|
|while|建立 [while](/dotnet/csharp/language-reference/keywords/while) 迴圈。|在方法、索引子、屬性存取子或事件存取子內。|

## <a name="see-also"></a>另請參閱

- [程式碼片段函式](../ide/code-snippet-functions.md)
- [程式碼片段](../ide/code-snippets.md)
- [範本參數](../ide/template-parameters.md)
- [如何：使用範圍語句程式碼片段](../ide/how-to-use-surround-with-code-snippets.md)
