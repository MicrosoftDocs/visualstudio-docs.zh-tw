---
title: CA1500:變數名稱不應該與欄位名稱相符 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8dc15c95398ed45954c3830d1c558a6653a4346f
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649963"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500:變數名稱不應該與欄位名稱相符
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新文件，請參閱[CA1500:變數名稱不應該與欄位名稱相符](https://docs.microsoft.com/visualstudio/code-quality/ca1500-variable-names-should-not-match-field-names)。  
  
|||  
|-|-|  
|TypeName|VariableNamesShouldNotMatchFieldNames|  
|CheckId|CA1500|  
|分類|Microsoft.Maintainability|  
|中斷變更|當引發與欄位具有相同名稱的參數：<br /><br /> -不間斷-如果外部組件，不論您所做的變更，則無法看到的欄位 」 和 「 將參數宣告的方法。<br />-中斷-如果您變更欄位的名稱，而且可以看到外部組件。<br />-中斷-如果您變更參數的名稱，並將其宣告的方法可以看到外部組件。<br /><br /> 當引發對做為欄位具有相同名稱的區域變數：<br /><br /> -不間斷-組件，不論您所做的變更之外無法看到的欄位。<br />-不間斷-如果您變更本機變數的名稱，並不會變更欄位的名稱。<br />-中斷-如果您變更欄位的名稱，而且它可被視為外部組件。|  
  
## <a name="cause"></a>原因  
 執行個體方法宣告參數或區域變數名稱符合宣告型別的執行個體欄位。 若要攔截違反規則的本機變數，必須建置測試的組件使用偵錯資訊和相關聯的程式資料庫 (.pdb) 檔案必須能夠使用。  
  
## <a name="rule-description"></a>規則描述  
 當執行個體欄位的名稱符合參數或區域變數名稱時，會使用來存取執行個體欄位`this`(`Me`在[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 之方法主體內的關鍵字。 當維護程式碼，很容易忘了這項差異，並假設參數/本機變數是指執行個體欄位中，會導致發生錯誤。 這是特別是針對冗長的方法主體，則為 true。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，重新命名的參數/變數或欄位。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 下列範例顯示兩個違反規則。  
  
 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/cs/FxCop.Maintainability.VarMatchesField.cs#1)]
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/vb/FxCop.Maintainability.VarMatchesField.vb#1)]
