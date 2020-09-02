---
title: Visual C# 程式碼片段 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- snippets [C#], default snippets
- snippets [C#], Code Snippet Inserter
- Code Snippet Inserter [J#]
- Code Snippet Inserter [C#]
- Visual C#, default snippets
ms.assetid: dbea3dd6-e650-4190-b874-c9f097d7de6e
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fb84854bd871277f680a753b28c17e3429283928
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646713"
---
# <a name="visual-c-code-snippets"></a>Visual C# 程式碼片段
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

程式碼片段是可快速插入程式碼的現成程式碼片段。 例如，`for` 程式碼片段會建立空白 `for` 迴圈。 部分程式碼片段是範圍陳述式程式碼片段，可讓您選取程式碼行，然後選擇包含所選取程式碼行的程式碼片段。 例如，如果您選取程式碼行，然後啟用 `for` 程式碼片段，則會建立迴圈區塊內包含這些程式碼行的 `for` 迴圈。 程式碼片段可以更快速、更輕鬆且更可靠地撰寫程式碼。

 您可以在游標位置插入程式碼片段，或在目前選取的程式碼周圍插入範圍陳述式程式碼片段。 程式碼片段插入器的叫用方式是透過 **IntelliSense** 功能表上的 [插入程式碼片段]**** 或 [範圍陳述式]**** 命令，或分別依序使用鍵盤快速鍵 CTRL+K 和 X 或是 CTRL+K 和 S。

 程式碼片段插入器會顯示所有可用程式碼片段的程式碼片段名稱。 程式碼片段插入器也會包含輸入對話方塊，您可以在其中輸入程式碼片段名稱或程式碼片段名稱的一部分。 程式碼片段插入器會反白顯示最接近程式碼片段名稱的相符項目。 任何時間按 TAB 都會關閉程式碼片段插入器，並插入目前選取的程式碼片段。 在程式碼編輯器中輸入 ESC 或按一下滑鼠會關閉程式碼片段插入器，而不插入程式碼片段。

## <a name="default-code-snippets"></a>預設程式碼片段
 Visual Studio 中預設會包含下列程式碼片段。

|名稱 (或捷徑)|描述|插入程式碼片段的有效位置|
|--------------------------|-----------------|---------------------------------------|
|#if|建立 [#if](https://msdn.microsoft.com/library/48cabbff-ca82-491f-a56a-eeccd528c7c2) 指示詞和 [#endif](https://msdn.microsoft.com/library/6a5fca55-5aee-441f-86f6-1c99fbe9ec05) 指示詞。|任何位置。|
|#region|建立 [#region](https://msdn.microsoft.com/library/672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4) 指示詞和 [#endregion](https://msdn.microsoft.com/library/16099660-91b2-49e5-9646-77f9ef069526) 指示詞。|任何位置。|
|~|建立包含類別的解構函式。|在類別內部。|
|屬性|建立衍生自 <xref:System.Attribute> 之類別的宣告。|在命名空間 (包含全域命名空間)、類別或結構內部。|
|checked|建立 [checked](https://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|Class - 類別|建立類別宣告。|在命名空間 (包含全域命名空間)、類別或結構內部。|
|ctor|建立包含類別的建構函式。|在類別內部。|
|cw|建立 <xref:System.Console.WriteLine%2A> 呼叫。|在方法、索引子、屬性存取子或事件存取子內。|
|do|建立[do](https://msdn.microsoft.com/library/50725f79-9ba6-4898-aa78-6e331568a1bb) `while` 迴圈。|在方法、索引子、屬性存取子或事件存取子內。|
|else|建立 [else](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|列舉|建立 [enum](https://msdn.microsoft.com/library/bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c) 宣告。|在命名空間 (包含全域命名空間)、類別或結構內部。|
|equals|建立覆寫 <xref:System.Object> 類別中所定義 <xref:System.Object.Equals%2A> 方法的方法宣告。|在類別或結構內部。|
|exception|建立衍生自例外狀況之類別的宣告 (預設為 <xref:System.Exception>)。|在命名空間 (包含全域命名空間)、類別或結構內部。|
|對象|建立 [for](https://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) 迴圈。|在方法、索引子、屬性存取子或事件存取子內。|
|foreach|建立 [foreach](https://msdn.microsoft.com/library/5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec) 迴圈。|在方法、索引子、屬性存取子或事件存取子內。|
|forr|建立在每個重複項目後遞減迴圈變數的 [for](https://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) 迴圈。|在方法、索引子、屬性存取子或事件存取子內。|
|if|建立 [if](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|索引子|建立索引子宣告。|在類別或結構內部。|
|interface|建立 [interface](https://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba) 宣告。|在命名空間 (包含全域命名空間)、類別或結構內部。|
|叫用|建立安全地叫用事件的區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|迭代器|建立迭代器。|在類別或結構內部。|
|iterindex|使用巢狀類別建立 "named" 迭代器和索引子組。|在類別或結構內部。|
|鎖定|建立 [lock](https://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|mbox|建立 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> 呼叫。 您可能需要新增 System.Windows.Forms.dll 的參考。|在方法、索引子、屬性存取子或事件存取子內。|
|namespace|建立 [namespace](https://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f) 宣告。|在命名空間 (包含全域命名空間) 內部。|
|prop|建立[自動實作的屬性](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7)宣告。|在類別或結構內部。|
|propfull|建立具有 get 和 set 存取子的屬性宣告。|在類別或結構內部。|
|propg|建立具有私用 "set" 存取子的唯讀[自動實作的屬性](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7)。|在類別或結構內部。|
|sim|建立 [static](https://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[int](https://msdn.microsoft.com/library/212447b4-5d2a-41aa-88ab-84fe710bdb52) Main 方法宣告。|在類別或結構內部。|
|struct|建立 [struct](https://msdn.microsoft.com/library/ff3dd9b7-dc93-4720-8855-ef5558f65c7c) 宣告。|在命名空間 (包含全域命名空間)、類別或結構內部。|
|svm|建立 [static](https://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[void](https://msdn.microsoft.com/library/0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4) Main 方法宣告。|在類別或結構內部。|
|switch|建立 [switch](https://msdn.microsoft.com/library/44bae8b8-8841-4d85-826b-8a94277daecb) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|嘗試|建立 [try-catch](https://msdn.microsoft.com/library/cb5503c7-bfa1-4610-8fc2-ddcd2e84c438) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|tryf|建立 [try-finally](https://msdn.microsoft.com/library/c27623fb-7261-4464-862c-7a369d3c8f0a) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|unchecked|建立 [unchecked](https://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|unsafe|建立 [unsafe](https://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) 區塊。|在方法、索引子、屬性存取子或事件存取子內。|
|using|建立 [using](https://msdn.microsoft.com/library/b42b8e61-5e7e-439c-bb71-370094b44ae8) 指示詞。|在命名空間 (包含全域命名空間) 內部。|
|while|建立 [while](https://msdn.microsoft.com/library/72a0765c-6852-4aca-b327-4a11cb7f5c59) 迴圈。|在方法、索引子、屬性存取子或事件存取子內。|

## <a name="see-also"></a>另請參閱
 [程式碼片段](../ide/code-snippet-functions.md)函式[程式碼片段](../ide/code-snippets.md)[如何：建立具有替代範本參數的新程式碼片段](https://msdn.microsoft.com/8d56d43c-097a-475b-aa85-cae1554b6338) [Template Parameters](../ide/template-parameters.md) [如何：使用範圍語句程式碼片段](../ide/how-to-use-surround-with-code-snippets.md)[如何：還原 c # 重構代碼](../ide/how-to-restore-csharp-refactoring-snippets.md)段
