---
title: CA2211：非固定欄位不應該為可見的 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa67c33eac5d618c0a080323720775beea7b68c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548209"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211:非常數欄位不應該為可見的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|類別|Microsoft. 使用量|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的靜態欄位不是常數，也不是唯讀的。

## <a name="rule-description"></a>規則描述
 既非常數，亦非唯讀的靜態欄位不是安全執行緒。 對這類欄位的存取權必須謹慎控制，且需要先進的程式設計技巧來同步處理對類別物件的存取。 因為這些是難以學習和主要的技巧，而測試這類物件會帶來自己的挑戰，所以靜態欄位最適合用來儲存不會變更的資料。 此規則適用于程式庫;應用程式不應該公開任何欄位。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將靜態欄位設為常數或唯讀。 如果無法這麼做，請重新設計類型以使用替代機制，例如可管理對基礎欄位之安全線程存取的安全線程屬性。 請注意，鎖定爭用和鎖死等問題可能會影響程式庫的效能和行為。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您正在開發應用程式，因此可以放心地隱藏此規則的警告，因此可以完全掌控包含靜態欄位的類型。 程式庫設計工具不應該隱藏此規則的警告;使用非固定靜態欄位可能會讓開發人員難以正確使用程式庫。

## <a name="example"></a>範例
 下列範例顯示違反此規則的類型。

 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/cs/FxCop.Usage.AvoidStaticNonConstants.cs#1)]
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/vb/FxCop.Usage.AvoidStaticNonConstants.vb#1)]
