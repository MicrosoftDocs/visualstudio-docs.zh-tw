---
title: Ca2000： 必須在超出範圍前處置物件 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 878c016f718693210a196d687ebe520b20cf277a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500522"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000：必須在超出範圍前處置物件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposeObjectsBeforeLosingScope|  
|CheckId|CA2000|  
|分類|Microsoft.Reliability|  
|中斷變更|非重大|  
  
## <a name="cause"></a>原因  
 本機物件<xref:System.IDisposable>建立型別，但是物件的所有參考都都超出範圍之前，不會處置物件。  
  
## <a name="rule-description"></a>規則描述  
 如果所有參考都都超出範圍之前，不會明確處置可處置的物件，則會處置物件，當記憶體回收行程執行完成項物件的某個不定時間點。 因為發生例外事件可能會導致無法完成項執行的物件，該物件應該改以明確處置。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，呼叫<xref:System.IDisposable.Dispose%2A>物件給它的所有參考都都超出範圍之前。  
  
 請注意，您可以使用`using`陳述式 (`Using`中[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 來包裝物件，可實作`IDisposable`。 物件會包裝在這種方式，自動將在處置`using`區塊。  
  
 以下是某些情況下，使用陳述式尚不足以保護 IDisposable 物件，並導致 ca2000 必須在超出發生。  
  
-   傳回可處置的物件需要建構物件時，是在 try/finally 區塊外部使用區塊。  
  
-   初始化可處置物件的成員不應該在執行中的建構函式的 using 陳述式。  
  
-   巢狀只能有一個例外狀況處理常式所保護的建構函式。 例如，套用至物件的  
  
    ```  
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))  
    { ... }  
    ```  
  
     會導致 ca2000 必須在超出發生，因為在 StreamReader 物件建構失敗可能會導致永遠不會關閉 FileStream 物件。  
  
-   動態物件應該實作 Dispose 模式的 IDisposable 物件使用陰影物件。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 除非您已在呼叫 `Dispose` 的物件上呼叫方法，例如 <xref:System.IO.Stream.Close%2A>，或是引發警告的方法傳回的 IDisposable 物件會包裝您的物件，否則請勿隱藏這項規則的警告。  
  
## <a name="related-rules"></a>相關的規則  
 [CA2213：可處置的欄位應該受到處置](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2202：不要多次處置物件](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)  
  
## <a name="example"></a>範例  
 如果您要實作的方法，傳回可處置的物件，使用 try/finally 區塊沒有 catch 區塊，藉此確定物件已處置。 藉由使用 try/finally 區塊，您可以允許在錯誤點引發，並確定在處置該物件的例外狀況。  
  
 在 OpenPort1 方法中，開啟 ISerializable 物件 SerialPort 呼叫或 SomeMethod 的呼叫可能會失敗。 Ca2000 必須在超出警告會在此實作中引發。  
  
 在 OpenPort2 方法中，兩個序列連接埠物件會宣告並設定為 null:  
  
-   `tempPort`用來測試方法作業都成功。  
  
-   `port`它用於方法的傳回值。  
  
 `tempPort`建構，並在中開啟`try`區塊，以及任何其他必要的工作在同一個執行`try`區塊。 在結尾`try`區塊中，開啟的通訊埠指派給`port`會傳回的物件和`tempPort`物件設定為`null`。  
  
 `finally`區塊會檢查值`tempPort`。 如果不是 null，此方法中的作業失敗，並`tempPort`關閉以確定會釋放任何資源。 如果方法的作業成功，或如果作業失敗，將會是 null，傳回的連接埠物件將包含開啟的 SerialPort 物件。  
  
 [!code-csharp[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/cs/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.cs#1)]
 [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vb#1)]
 [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vboverflow.vb#1)]  
  
## <a name="example"></a>範例  
 根據預設，[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]編譯器有溢位檢查的所有算術運算子。 因此，任何 Visual Basic 算術運算可能會擲回<xref:System.OverflowException>。 這可能會導致非預期的違規，例如 ca2000 必須在超出規則中。 例如，下列 CreateReader1 函式會產生 ca2000 必須在超出違規，因為 Visual Basic 編譯器發出的溢位檢查可能會擲回例外狀況會導致不是用來處置 StreamReader 加法的指示。  
  
 若要修正此問題，您可以停用的溢位檢查發出 Visual Basic 編譯器在您的專案或您可以修改您的程式碼，如下列 CreateReader2 函式所示。  
  
 停用發出溢位檢查，以滑鼠右鍵按一下方案總管] 中的專案名稱，然後按一下 [**屬性**。 按一下 **編譯**，按一下**進階編譯選項**，然後核取**移除整數溢位檢查**。  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  -->  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IDisposable>   
 [Dispose 模式](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)