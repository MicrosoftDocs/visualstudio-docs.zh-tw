---
title: CA1809：避免過多的區域變數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d23d9cc6006997c82451ac061e3ee0353e59b1b9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671488"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809：避免使用過多區域變數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Category|Microsoft。效能|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 成員包含超過64個區域變數，其中有些可能是由編譯器所產生。

## <a name="rule-description"></a>規則描述
 常見的效能優化是將值儲存在處理器暫存器中，而不是在記憶體中，這稱為*enregistering*值。 通用語言執行時間會考慮最多64個區域變數來進行 enregistration。 未 enregistered 的變數會放在堆疊上，而且必須在操作之前移動到暫存器。 若要允許所有區域變數都 enregistered，請將本機變數的數目限制為64。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請重構該執行，以使用不超過64的區域變數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果效能不是問題，可以放心地隱藏此規則的警告，或停用規則。

## <a name="related-rules"></a>相關規則
 [CA1804：必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)
