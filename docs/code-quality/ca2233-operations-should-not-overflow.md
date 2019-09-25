---
title: CA2233:運算不應該發生溢位
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b99aae681dbe7bbeece557a15d78aed0b3f07f6f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230823"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233:運算不應該發生溢位

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|分類|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因

方法會執行算數運算，而且不會事先驗證運算元以避免溢位。

## <a name="rule-description"></a>規則描述

請勿在未先驗證運算元的情況下執行算數運算，以確定作業的結果不在相關資料類型的可能值範圍外。 視執行內容和涉及的資料類型而定，算術溢位可能會導致<xref:System.OverflowException?displayProperty=fullName>結果的或最重要的部分被捨棄。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請在執行作業之前驗證運算元。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果運算元的可能值永遠不會造成算數運算溢位，則可以安全地隱藏此規則的警告。

## <a name="example-of-a-violation"></a>違規的範例

下列範例中的方法會操控違反此規則的整數。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]需要停用 [**移除**整數溢位] 選項，才會引發。

[!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
[!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]

如果傳遞<xref:System.Int32.MinValue?displayProperty=fullName>此範例中的方法，作業將會下溢。 這會導致捨棄結果的最高有效位。 下列程式碼會示範這種情況。

```csharp
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

```vb
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

輸出：

```text
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>修正輸入參數驗證

下列範例會藉由驗證輸入的值來修正先前的違規。

[!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
[!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]

## <a name="fix-with-a-checked-block"></a>使用已檢查的區塊修正

下列範例會藉由在已檢查的區塊中包裝作業來修正先前的違規。 如果作業造成溢位， <xref:System.OverflowException?displayProperty=fullName>則會擲回。

中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]不支援已檢查的區塊。

[!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>開啟核取的算術溢位/下溢

如果您在中C#開啟核取的算術溢位/下溢，它就相當於將每個整數運算包裝在已檢查的區塊中。

若要在中C#開啟核取的算術溢位/下溢：

1. 在**方案總管**中，以滑鼠右鍵按一下您的專案，然後選擇 [**屬性**]。

2. 選取 [建置] 索引標籤，然後按一下 [進階]。

3. 選取 [**檢查算術溢位/下溢**]，然後按一下 **[確定]** 。

## <a name="see-also"></a>另請參閱

- <xref:System.OverflowException?displayProperty=fullName>
- [C# 運算子](/dotnet/csharp/language-reference/operators/index)
- [Checked 與 Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)