---
title: CA2000：在遺失範圍之前處置物件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e3de3246980ead0b20d471321a9696451aed81ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534767"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000:必須在超出範圍前處置物件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|類別|Microsoft 可靠性|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 <xref:System.IDisposable>系統會建立類型的區域物件，但物件不會在物件的所有參考都超出範圍之前處置。

## <a name="rule-description"></a>規則描述
 如果可處置物件在所有的參考都超出範圍之前未明確處置，則當垃圾收集行程執行物件的完成項時，將會在某些不定時間處置物件。 因為可能會發生例外狀況事件而導致物件的完成項無法執行，所以應改為明確地處置物件。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請 <xref:System.IDisposable.Dispose%2A> 在物件的所有參考都超出範圍之前呼叫物件。

 請注意，您可以使用 `using`) 中的語句 (`Using` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 來包裝執行的物件 `IDisposable` 。 以這種方式包裝的物件將會自動在區塊結尾處處置 `using` 。

 以下是 using 語句不足以保護 IDisposable 物件，而且可能會造成 CA2000 的情況。

- 傳回可處置的物件需要在 using 區塊以外的 try/finally 區塊中建立物件。

- 在 using 語句的函式中，不應完成初始化可處置物件的成員。

- 僅由一個例外狀況處理常式所保護的函式進行嵌套。 例如，

    ```
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
    { ... }
    ```

     導致 CA2000 發生，因為 StreamReader 物件的結構中發生失敗，導致 FileStream 物件永遠無法關閉。

- 動態物件應使用陰影物件來執行 IDisposable 物件的處置模式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 除非您已在呼叫 `Dispose` 的物件上呼叫方法，例如 <xref:System.IO.Stream.Close%2A>，或是引發警告的方法傳回的 IDisposable 物件會包裝您的物件，否則請勿隱藏這項規則的警告。

## <a name="related-rules"></a>相關規則
 [CA2213:可處置的欄位應該受到處置](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2202:不要多次處置物件的 Dispose 方法](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>範例
 如果您要執行的方法會傳回可處置的物件，請在沒有 catch 區塊的情況下使用 try/finally 區塊，以確保物件已處置。 藉由使用 try/finally 區塊，您可允許在錯誤點引發例外狀況，並確保物件已處置。

 在 OpenPort1 方法中，開啟 ISerializable 物件 SerialPort 或 SomeMethod 呼叫的呼叫可能會失敗。 這項實行會引發 CA2000 警告。

 在 OpenPort2 方法中，會宣告兩個 SerialPort 物件，並將其設定為 null：

- `tempPort`，用來測試方法作業是否成功。

- `port`，用於方法的傳回值。

  `tempPort`會在區塊中建立和開啟 `try` ，而任何其他必要的工作則會在相同的 `try` 區塊中執行。 在區塊的結尾，會將 `try` 開啟的埠指派給 `port` 將傳回的物件，並將 `tempPort` 物件設定為 `null` 。

  `finally`區塊會檢查的值 `tempPort` 。 如果它不是 null，則方法中的作業已失敗，並已 `tempPort` 關閉以確定已釋放任何資源。 如果方法的作業成功，傳回的埠物件將會包含開啟的 SerialPort 物件，如果作業失敗，則會是 null。

  [!code-csharp[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/cs/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.cs#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vb#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vboverflow.vb#1)]

## <a name="example"></a>範例
 根據預設， [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 編譯器會檢查溢位的所有算術運算子。 因此，任何 Visual Basic 的算數運算都可能會擲回 <xref:System.OverflowException> 。 這可能會導致 CA2000 之類的規則發生非預期的違規。 例如，下列 CreateReader1 函式會產生 CA2000 違規，因為 Visual Basic 編譯器會發出溢位檢查指令，以進行加法，而這可能會擲回造成 StreamReader 無法處置的例外狀況。

 若要修正此問題，您可以在專案中停用 Visual Basic 編譯器發出溢位檢查，或修改您的程式碼，如下列 CreateReader2 函數所示。

 若要停用發出溢位檢查，請在方案總管中的專案名稱上按一下滑鼠右鍵，然後按一下 [ **屬性**]。 按一下 [ **編譯**]，再按一下 [ **Advanced Compile Options**]，然後選取 [ **移除整數溢位檢查**]。

<!-- TODO: review snippet reference  [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  -->

## <a name="see-also"></a>另請參閱
 <xref:System.IDisposable>[Dispose 模式](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)