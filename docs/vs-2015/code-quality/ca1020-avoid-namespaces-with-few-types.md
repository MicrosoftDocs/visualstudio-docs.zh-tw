---
title: CA1020：避免具有少數類型的命名空間 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 81eaf2735869668b86ca8879478e3d76d77a2811
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662316"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020：避免在命名空間中包含過少的類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Category|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 全域命名空間以外的命名空間包含少於五個類型。

## <a name="rule-description"></a>規則描述
 請確定每個命名空間都有邏輯組織，而且有一個有效的原因，就是將類型放在稀疏填入的命名空間中。 命名空間應該包含在大部分情況下一起使用的類型。 當其應用程式互斥時，類型應該位於不同的命名空間。 例如，<xref:System.Web.UI> 命名空間包含 Web 應用程式中所使用的類型，而 <xref:System.Windows.Forms> 命名空間包含用於 [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] 架構應用程式中的類型。 雖然這兩個命名空間都有可控制使用者介面層面的類型，但這些類型並不是設計用於相同的應用程式中。 因此，它們位於不同的命名空間。 仔細命名空間組織也會很有説明，因為它會增加功能的可搜尋性。 藉由檢查命名空間階層，程式庫取用者應該能夠找出用來執行功能的類型。

> [!NOTE]
> 設計階段類型和許可權不應合併到其他命名空間，以符合此指導方針。 這些類型屬於您主要命名空間底下的專屬命名空間，而命名空間的結尾應該是 `.Design`，而 `.Permissions`。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請嘗試將只包含幾種類型的命名空間結合成單一命名空間。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當命名空間不包含與其他命名空間中的類型搭配使用的類型時，可以安全地隱藏此規則的警告。
