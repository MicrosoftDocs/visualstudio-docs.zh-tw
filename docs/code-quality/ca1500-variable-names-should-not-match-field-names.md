---
title: CA1500：變數名稱不應該與欄位名稱相符
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3f7e8b0021fc3c318389aa3d6d3f53391b71351f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443975"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500：變數名稱不應該與欄位名稱相符

|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|分類|Microsoft。可維護性|
|重大變更|在與欄位同名的參數上引發時：<br /><br /> -非中斷-如果宣告參數的欄位和方法無法在元件外部看到，不論您所做的變更為何。<br />-中斷-如果您變更欄位的名稱，而且可以在元件外部看到。<br />-中斷-如果您變更參數的名稱，以及可在元件外部看到其宣告的方法。<br /><br /> 在與欄位同名的本機變數上引發時：<br /><br /> -非中斷-如果在元件外部看不到欄位，不論您所做的變更為何。<br />-非中斷-如果您變更本機變數的名稱，而不變更欄位的名稱。<br />-中斷-如果您變更欄位的名稱，它可以在元件外部看到。|

## <a name="cause"></a>原因

實例方法會宣告參數或區域變數，其名稱符合宣告類型的實例欄位。 若要攔截違反規則的區域變數，必須使用偵錯工具建立已測試的元件，而且必須要有相關聯的程式資料庫（.pdb）檔案。

## <a name="rule-description"></a>規則描述

當實例欄位的名稱符合參數或區域變數名稱時，在方法主體內時，會使用 `this` （[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]）關鍵字中的 @no__t 來存取實例欄位。 維護程式碼時，很容易忘記這種差異，並假設參數/區域變數參考實例欄位，這會導致錯誤。 這種情況特別適用于冗長的方法主體。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請重新具名引數/變數或欄位。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="example"></a>範例

下列範例顯示兩個規則違規。

[!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
[!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]
