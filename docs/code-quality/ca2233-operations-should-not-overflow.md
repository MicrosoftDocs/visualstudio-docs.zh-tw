---
title: "CA2233： 運算應該不發生溢位 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f5d048476997517a835337b568930367f97c2c92
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233：運算不應該發生溢位
|||  
|-|-|  
|TypeName|OperationsShouldNotOverflow|  
|CheckId|CA2233|  
|分類|Microsoft.Usage|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 方法執行算術運算，而且不會驗證運算元事先以防止溢位。  
  
## <a name="rule-description"></a>規則描述  
 應該先驗證運算元，以確定作業的結果不相關的資料類型的可能值的範圍外執行算術運算。 根據執行內容和相關的資料類型，算術溢位可能會導致 <xref:System.OverflowException?displayProperty=fullName>或捨棄結果的最大顯著性位元。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請執行作業之前驗證運算元。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，如果運算元的可能值將永遠不會導致算術溢位運算。  
  
## <a name="example-of-a-violation"></a>發生違規的範例  
  
### <a name="description"></a>描述  
 下列範例中的方法操作違反此規則的整數。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]需要**移除**整數溢位選項停用這個引發。  
  
### <a name="code"></a>程式碼  
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]  
  
### <a name="comments"></a>註解  
 如果在此範例中對方法傳遞<xref:System.Int32.MinValue?displayProperty=fullName>，作業會反向溢位。 這會導致捨棄結果的最大顯著性位元。 下列程式碼會示範如何發生這種情況。  
  
 [C#]  
  
```  
public static void Main()  
{  
    int value = int.MinValue;    // int.MinValue is -2147483648   
    value = Calculator.Decrement(value);   
    Console.WriteLine(value);  
}  
```  
  
 [VB]  
  
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
  
## <a name="fix-with-input-parameter-validation"></a>修正 輸入的參數驗證  
  
### <a name="description"></a>描述  
 下列範例會驗證輸入的值，以修正上述違規。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]  
  
## <a name="fix-with-a-checked-block"></a>修正檢查區塊  
  
### <a name="description"></a>描述  
 下列範例會藉由檢查區塊中包裝作業修正上述違規。 如果作業造成溢位，<xref:System.OverflowException?displayProperty=fullName>就會擲回。  
  
 請注意，不支援已檢查的區塊中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]  
  
## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>開啟 檢查算術溢位/反向溢位  
 如果您開啟檢查算術溢位/反向溢位在 C# 中，它相當於在檢查區塊包裝每個整數運算。  
  
 **檢查算術溢位/反向溢位在 C# 中開啟**  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下您的專案，然後選擇 [**屬性**。  
  
2.  選取 [建置] 索引標籤，然後按一下 [進階]。  
  
3.  選取**算術溢位/反向溢位檢查**按一下**確定**。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.OverflowException?displayProperty=fullName>   
 [C# 運算子](/dotnet/csharp/language-reference/operators/index)   
 [Checked 與 Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)