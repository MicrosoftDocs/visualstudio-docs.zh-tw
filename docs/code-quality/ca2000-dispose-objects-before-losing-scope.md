---
title: CA2000:必須在超出範圍前處置物件
ms.date: 05/14/2019
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7a498a01741b86c16a52f790489dc8ce62aad06c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233234"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000:必須在超出範圍前處置物件

|||
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|分類|Microsoft.Reliability|
|重大變更|不中斷|

## <a name="cause"></a>原因

系統會建立<xref:System.IDisposable>類型的本機物件，但在物件的所有參考都超出範圍之前，不會處置物件。

## <a name="rule-description"></a>規則描述

如果可處置物件未在其所有參考超出範圍之前明確處置，則當垃圾收集行程執行物件的完成項時，將會在某些不定的時間處置物件。 因為可能會發生例外狀況事件，而導致無法執行物件的完成項，所以應改為明確處置物件。

### <a name="special-cases"></a>特殊案例

即使未處置物件，也不會針對下列類型的本機物件引發規則 CA2000 必須：

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

將其中一種類型的物件傳遞至函式，然後將它指派給欄位，表示*處置擁有權傳送*至新建立的類型。 也就是說，新建立的型別現在負責處置物件。 如果您的程式碼將其中一種類型的物件傳遞至函式，則即使在物件的所有參考都超出範圍之前未處置，也不會違反規則 CA2000 必須。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形， <xref:System.IDisposable.Dispose%2A>請在物件的所有參考都超出範圍之前，對其呼叫。

您可以使用[ `using`語句](/dotnet/csharp/language-reference/keywords/using-statement)（[`Using`](/dotnet/visual-basic/language-reference/statements/using-statement)在 Visual Basic 中）來包裝可執行<xref:System.IDisposable>的物件。 以這種方式包裝的物件會在`using`區塊結尾自動處置。 不過，下列情況不應或無法使用`using`語句來處理：

- 若要傳回可處置的物件，物件必須在`try/finally` `using`區塊外的區塊中進行結構化。

- 請勿在`using`語句的函式中初始化可處置物件的成員。

- 當只受一個例外狀況處理常式保護的函式被嵌套在[ `using`語句](/dotnet/csharp/language-reference/language-specification/statements#the-using-statement)的取得部分時，外部函式中的失敗可能會導致不會關閉嵌套的函式所建立的物件。 在下列範例中，在此函式<xref:System.IO.StreamReader>中的失敗可能會<xref:System.IO.FileStream>導致物件永遠無法關閉。 在此情況下，CA2000 必須會旗標違反規則。

   ```csharp
   using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
   { ... }
   ```

- 動態物件應使用陰影物件來執行<xref:System.IDisposable>物件的處置模式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告，除非：

- 您已在呼叫`Dispose`的物件上呼叫方法，例如<xref:System.IO.Stream.Close%2A>
- 引發警告<xref:System.IDisposable>的方法會傳回包裝物件的物件。
- 配置方法沒有處置擁有權;也就是說，處置物件的責任會傳送至在方法中建立並傳回給呼叫者的另一個物件或包裝函式

## <a name="related-rules"></a>相關規則

- [CA2213：可處置的欄位應該受到處置](../code-quality/ca2213-disposable-fields-should-be-disposed.md)
- [CA2202不要多次處置物件](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>範例

如果您要執行的方法會傳回可處置的物件，請使用沒有 catch 區塊的 try/finally 區塊，以確定物件已被處置。 藉由使用 try/finally 區塊，您允許在錯誤點引發例外狀況，並確定物件已處置。

在 OpenPort1 方法中，開啟 ISerializable 物件 SerialPort 或呼叫 SomeMethod 的呼叫可能會失敗。 此執行會引發 CA2000 必須警告。

在 OpenPort2 方法中，會宣告兩個 SerialPort 物件，並將其設定為 null：

- `tempPort`，用來測試方法作業是否成功。

- `port`，用於方法的傳回值。

會在區塊中進行結構化和開啟，而任何其他必要的工作則會在`try`相同的區塊中執行。 `try` `tempPort` 在`try`區塊的結尾，已開啟的埠會指派`port`給`tempPort`將傳回的物件，並將物件設定為`null`。

區塊會檢查的`tempPort`值。 `finally` 如果不是 null，則方法中的作業會失敗，而且`tempPort`會關閉以確保釋放任何資源。 如果方法的作業成功，則傳回的埠物件會包含已開啟的 SerialPort 物件，如果作業失敗，則會是 null。

```csharp
public SerialPort OpenPort1(string portName)
{
   SerialPort port = new SerialPort(portName);
   port.Open();  //CA2000 fires because this might throw
   SomeMethod(); //Other method operations can fail
   return port;
}

public SerialPort OpenPort2(string portName)
{
   SerialPort tempPort = null;
   SerialPort port = null;
   try
   {
      tempPort = new SerialPort(portName);
      tempPort.Open();
      SomeMethod();
      //Add any other methods above this line
      port = tempPort;
      tempPort = null;

   }
   finally
   {
      if (tempPort != null)
      {
         tempPort.Close();
      }
   }
   return port;
}
```

```vb
Public Function OpenPort1(ByVal PortName As String) As SerialPort

   Dim port As New SerialPort(PortName)
   port.Open()    'CA2000 fires because this might throw
   SomeMethod()   'Other method operations can fail
   Return port

End Function

Public Function OpenPort2(ByVal PortName As String) As SerialPort

   Dim tempPort As SerialPort = Nothing
   Dim port As SerialPort = Nothing

   Try
      tempPort = New SerialPort(PortName)
      tempPort.Open()
      SomeMethod()
      'Add any other methods above this line
      port = tempPort
      tempPort = Nothing

   Finally
      If Not tempPort Is Nothing Then
         tempPort.Close()
      End If

   End Try

   Return port

End Function
```

## <a name="example"></a>範例

根據預設，Visual Basic 編譯器會檢查溢位的所有算術運算子。 因此，任何 Visual Basic 的算數運算都可能<xref:System.OverflowException>會擲回。 這可能會導致規則中發生未預期的違規，例如 CA2000 必須。 例如，下列 CreateReader1 函式會產生 CA2000 必須違規，因為 Visual Basic 編譯器會針對加法引發溢位檢查指令，而這可能會擲回例外狀況，而導致無法處置 StreamReader。

若要修正這個問題，您可以停用專案中 Visual Basic 編譯器發出溢位檢查的情況，也可以修改程式碼，如下列 CreateReader2 函數所示。

若要停用發出溢位檢查，請在方案總管中的專案名稱上按一下滑鼠右鍵，然後按一下 [**屬性**]。 按一下 [**編譯**]，再按一下 [ **Advanced compile Options**]，然後選取 [**移除整數溢位檢查**]。

[!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>另請參閱

- <xref:System.IDisposable>
- [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)