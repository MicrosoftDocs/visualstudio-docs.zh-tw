---
title: CA1822：將成員標記為靜態 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a571be6b713cd59ca290906e9398b78c8c021ba8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661172"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822：將成員標記為靜態
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新檔，請參閱[CA1822：將成員標記為靜態](https://docs.microsoft.com/visualstudio/code-quality/ca1822-mark-members-as-static)。

|||
|-|-|
|TypeName|MarkMembersAsStatic|
|CheckId|CA1822|
|Category|Microsoft。效能|
|中斷變更|不中斷-如果在元件外部看不到成員，不論您所做的變更為何。<br /><br /> 不中斷-如果您只是使用 `this` 關鍵字將成員變更為實例成員。<br /><br /> 中斷-如果您將成員從實例成員變更為靜態成員，而且它在元件外部是可見的。|

## <a name="cause"></a>原因
 未存取實例資料的成員未標記為靜態（在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 中為 Shared）。

## <a name="rule-description"></a>規則描述
 不會存取執行個體資料或不會呼叫執行個體方法的成員，可以標記為 static (在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 中為 Shared)。 將方法標記為 static 之後，編譯器將對這些成員發出非虛擬呼叫位置。 發出非虛擬的呼叫位置，將可防止每個呼叫的執行時間檢查，以確保目前的物件指標為非 null。 這麼做可讓效能敏感的程式碼獲得顯著的效能提升。 在某些情況下，存取目前物件實例的失敗表示正確性的問題。

## <a name="how-to-fix-violations"></a>如何修正違規
 將成員標記為靜態（或在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 中共用），或在方法主體中使用 ' this '/' Me ' （如果適用的話）。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 針對先前出貨的程式碼，您可以放心地隱藏此規則中的警告，這是一項重大變更。

## <a name="related-rules"></a>相關規則
 [CA1811：避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812：避免使用未執行個體化的內部類別](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804：必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)
