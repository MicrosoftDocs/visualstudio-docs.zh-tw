---
title: CA2211:非常數欄位不應該為可見的
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 77253de14219c4c1c6737f9bc6e5c61e11fff4ba
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937461"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211:非常數欄位不應該為可見的

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|分類|Microsoft.Usage|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的靜態欄位不是常數，也不是唯讀的。

## <a name="rule-description"></a>規則描述
 既非常數，亦非唯讀的靜態欄位不是安全執行緒。 這類欄位存取必須小心控制，並需要進階的程式設計技巧來同步處理類別物件的存取權。 因為這些都是很困難的技巧，以了解並精通，而測試這類物件會帶來獨有的挑戰，靜態欄位是最適合用於儲存不會變更的資料。 此規則會套用至程式庫;應用程式不應該公開的任何欄位。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，讓靜態欄位常數或唯讀狀態。 如果這不可行，重新設計要使用的替代機制，例如管理執行緒安全的基礎欄位的存取具備執行緒安全屬性的型別。 了解問題，例如鎖定爭用的情況和死結 （deadlock），可能會影響效能和程式庫行為。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可以安全地隱藏此規則的警告，如果您正在開發應用程式，因此有 完全控制存取包含靜態欄位的型別。 程式庫設計人員不應該隱藏這個規則; 的警告使用非常數的靜態欄位，可以使用程式庫開發人員很難正確使用。

## <a name="example"></a>範例
 下列範例顯示違反此規則的型別。

 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]