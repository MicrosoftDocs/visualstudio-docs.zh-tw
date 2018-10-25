---
title: CA2233：運算不應該發生溢位
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 73c0e616eb527a2213c77cdae00c42635d49b130
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938899"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233：運算不應該發生溢位

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

方法會執行算術運算，並不會驗證運算元事先以避免溢位。

## <a name="rule-description"></a>規則描述

不執行算術運算，而不先驗證運算元，以確定作業的結果不相關的資料類型的可能值的範圍之外。 根據執行內容和相關的資料類型，算術溢位可能會導致其中一個<xref:System.OverflowException?displayProperty=fullName>或捨棄結果的最大顯著性的位元。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請驗證運算元，才能執行此作業。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可安全地隱藏此規則的警告，如果運算元的可能值絕不會造成算術溢位運算。

## <a name="example-of-a-violation"></a>發生違規的範例

下列範例中的方法操作違反此規則的整數。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 需要**移除**整數溢位選項來停用這個來引發。

[!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
[!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]

如果在此範例中的方法傳遞<xref:System.Int32.MinValue?displayProperty=fullName>，作業會反向溢位。 這會導致捨棄結果的最大顯著性位元。 下列程式碼顯示如何發生這種情況。

```csharp
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

```vb
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

輸出：

```text
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>修正 輸入的參數驗證

下列範例會驗證輸入的值，以修正先前的違規。

[!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
[!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]

## <a name="fix-with-a-checked-block"></a>修正已核取的區塊

下列範例會藉由已檢查的區塊中包裝作業修正上述的違規。 如果作業造成溢位，<xref:System.OverflowException?displayProperty=fullName>就會擲回。

中不支援已檢查的區塊[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]。

[!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>開啟 檢查算術溢位/反向溢位

如果您開啟 檢查算術溢位/反向溢位在 C# 中，它就相當於每個整數作業包裝在檢查的區塊。

若要開啟 檢查算術溢位/反向溢位在 C# 中：

1.  在 **方案總管**，以滑鼠右鍵按一下您的專案，然後選擇**屬性**。

2.  選取 [建置] 索引標籤，然後按一下 [進階]。

3.  選取 **檢查算術溢位/反向溢位**然後按一下**確定**。

## <a name="see-also"></a>另請參閱

- <xref:System.OverflowException?displayProperty=fullName>
- [C# 運算子](/dotnet/csharp/language-reference/operators/index)
- [Checked 與 Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)