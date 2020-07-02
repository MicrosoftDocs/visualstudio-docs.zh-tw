---
title: CA2233 運算：作業不應該溢位 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: eff09fb8f4423560c4681c94507d909f5864c69e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545232"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233:運算不應該發生溢位
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|類別|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 方法會執行算數運算，而且不會事先驗證運算元以避免溢位。

## <a name="rule-description"></a>規則描述
 不應該先驗證運算元來執行算數運算，以確定作業的結果不在相關資料類型的可能值範圍外。 視執行內容和涉及的資料類型而定，算術溢位可能會導致 <xref:System.OverflowException?displayProperty=fullName> 結果的或最重要的部分被捨棄。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請在執行作業之前驗證運算元。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果運算元的可能值永遠不會造成算數運算溢位，則可以安全地隱藏此規則的警告。

## <a name="example-of-a-violation"></a>違規的範例

### <a name="description"></a>描述
 下列範例中的方法會操控違反此規則的整數。 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]需要停用 [**移除**整數溢位] 選項，才會引發。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>註解
 如果傳遞此範例中的方法 <xref:System.Int32.MinValue?displayProperty=fullName> ，作業將會下溢。 這會導致捨棄結果的最高有效位。 下列程式碼會示範這種情況。

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 VB

```
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

### <a name="output"></a>輸出

```
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>修正輸入參數驗證

### <a name="description"></a>描述
 下列範例會藉由驗證輸入的值來修正先前的違規。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>使用已檢查的區塊修正

### <a name="description"></a>描述
 下列範例會藉由在已檢查的區塊中包裝作業來修正先前的違規。 如果作業造成溢位，則會擲回 <xref:System.OverflowException?displayProperty=fullName> 。

 請注意，中不支援已檢查的區塊 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>開啟核取的算術溢位/下溢
 如果您開啟 c # 中的已檢查算術溢位/下溢，它就相當於將每個整數運算包裝在已檢查的區塊中。

 **若要開啟 C 中的已檢查算術溢位/下溢#**

1. 在**方案總管**中，以滑鼠右鍵按一下您的專案，然後選擇 [**屬性**]。

2. 選取 [建置]**** 索引標籤，然後按一下 [進階]****。

3. 選取 [**檢查算術溢位/下溢**]，然後按一下 **[確定]**。

## <a name="see-also"></a>另請參閱
 <xref:System.OverflowException?displayProperty=fullName>[已檢查並取消核](https://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e)取[c # 運算子](https://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)
