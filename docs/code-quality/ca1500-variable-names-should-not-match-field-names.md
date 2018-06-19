---
title: CA1500：變數名稱不應該與欄位名稱相符
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa5c015205b5e325cfba06bb433c44ecc0631d5b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917026"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500：變數名稱不應該與欄位名稱相符
|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|分類|Microsoft.Maintainability|
|中斷變更|當引發與欄位具有相同名稱的參數：<br /><br /> -非中斷-如果外部組件，不論您所進行的變更，則無法看到欄位和宣告該參數的方法。<br />-中斷-如果您變更欄位的名稱，而且可以看到組件之外。<br />-中斷-如果您變更參數的名稱，且會將其宣告的方法可以看到在組件外部。<br /><br /> 當引發與欄位具有相同名稱的本機變數：<br /><br /> -非中斷的組件，不論您所進行的變更之外無法看到的欄位。<br />-非中斷-如果您變更本機變數的名稱，並不會變更欄位的名稱。<br />-中斷-如果您變更欄位的名稱，並在組件外部看到它。|

## <a name="cause"></a>原因
 執行個體方法宣告的參數或區域變數，其名稱符合宣告類型的執行個體欄位。 若要攔截違反規則的本機變數，必須建立測試的組件使用偵錯資訊和相關聯的程式資料庫 (.pdb) 檔案必須能夠使用。

## <a name="rule-description"></a>規則描述
 當執行個體欄位的名稱符合的參數或區域變數名稱時，會使用來存取執行個體欄位`this`(`Me`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 之方法主體內的關鍵字。 當維護程式碼，很容易忘記這項差異，並假設參數/本機變數，是指執行個體欄位中，會導致發生錯誤。 這是特別為方法主體過於冗長，則為 true。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，重新命名的參數/變數或欄位。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會示範兩個規則的違規。

 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]