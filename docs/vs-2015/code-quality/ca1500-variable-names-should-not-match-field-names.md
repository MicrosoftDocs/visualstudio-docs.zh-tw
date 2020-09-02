---
title: CA1500：變數名稱不應該與功能變數名稱相符 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9565bc1ae3166c0475e8af7f0fde381497309b01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547910"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500:變數名稱不應該與欄位名稱相符
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新檔，請參閱 [CA1500：變數名稱不應該與功能變數名稱相符](/visualstudio/code-quality/ca1500-variable-names-should-not-match-field-names)。

|Item|值|
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|類別|Microsoft 的可維護性|
|中斷變更|在與欄位同名的參數上引發時：<br /><br /> -非中斷-如果在元件外部看不到宣告參數的欄位和方法，不論您所做的變更為何。<br />-中斷-如果您變更欄位的名稱，而且可以在元件外部看到。<br />-中斷-如果您變更參數的名稱和宣告的方法，則可以在元件外部看到。<br /><br /> 在與欄位同名的本機變數上引發時：<br /><br /> -非中斷-如果在元件外部看不到欄位，則不論您所做的變更為何。<br />-非中斷-如果您變更本機變數的名稱，而且不變更欄位的名稱。<br />-中斷-如果您變更欄位的名稱，它可以在元件外部看到。|

## <a name="cause"></a>原因
 實例方法宣告的參數或區域變數的名稱符合宣告類型的實例欄位。 若要捕捉違反規則的區域變數，則必須使用偵錯工具來建立已測試的元件，以及相關聯的程式資料庫 ( .pdb) 檔必須可用。

## <a name="rule-description"></a>規則描述
 當實例欄位的名稱符合參數或區域變數名稱時，會在 `this` `Me` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 方法主體內使用) 關鍵字中的 (來存取實例欄位。 維護程式碼時，很容易就會忘記這項差異，並假設參數/區域變數參考到實例欄位，這會導致錯誤。 這種情況特別適用于冗長的方法主體。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請重新具名引數/變數或欄位。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示兩個規則違規。

 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/cs/FxCop.Maintainability.VarMatchesField.cs#1)]
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/vb/FxCop.Maintainability.VarMatchesField.vb#1)]
