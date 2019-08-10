---
title: CA2211:非常數欄位不應該為可見的
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 77909627385a7aa2e41f87c23ec41dc8ac0e1a5e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920352"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211:非常數欄位不應該為可見的

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|分類|Microsoft.Usage|
|中斷變更|中斷|

## <a name="cause"></a>原因
公用或受保護的靜態欄位不是常數, 也不是唯讀的。

## <a name="rule-description"></a>規則描述
既非常數，亦非唯讀的靜態欄位不是安全執行緒。 對這類欄位的存取權必須謹慎控制, 而且需要先進的程式設計技巧來同步處理對類別物件的存取。 因為這些是難以學習和主控的技巧, 而測試這類物件會帶來自己的挑戰, 所以靜態欄位最適合用來儲存不會變更的資料。 此規則適用于程式庫;應用程式不應該公開任何欄位。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形, 請將靜態欄位設為常數或唯讀。 如果無法這麼做, 請重新設計類型以使用替代機制 (例如安全線程屬性) 來管理基礎欄位的執行緒安全存取。 請注意, 鎖定爭用和鎖死之類的問題可能會影響程式庫的效能和行為。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
如果您正在開發應用程式, 並可完全控制包含靜態欄位之類型的存取權, 就可以放心地隱藏此規則的警告。 程式庫設計工具不應該隱藏此規則的警告;使用非固定的靜態欄位可以讓開發人員不容易正確使用程式庫。

## <a name="example"></a>範例
下列範例顯示違反此規則的類型。

[!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
[!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]