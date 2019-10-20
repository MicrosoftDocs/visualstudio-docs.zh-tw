---
title: CA2103：審查命令式安全性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b4abf0b15a4fbba1abc61572da8a2f6126c754f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652151"
---
# <a name="ca2103-review-imperative-security"></a>CA2103：必須檢視命令式安全性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|Category|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法會使用命令式安全性，而且可能會利用只要要求正在使用中就可能變更的狀態資訊或傳回值建構權限。

## <a name="rule-description"></a>規則描述
 相較于宣告式安全性，命令式安全性會使用 managed 物件來指定程式碼執行期間的許可權和安全性動作，這會使用屬性來儲存中繼資料中的許可權和動作。 命令式安全性非常有彈性，因為您可以設定權限物件的狀態，並使用在執行時間之前無法使用的資訊來選取安全性動作。 這項彈性的風險在於，只要動作作用中，您用來判斷許可權狀態的執行時間資訊就不會保持不變。

 請盡可能使用宣告式安全性。 宣告式需求比較容易瞭解。

## <a name="how-to-fix-violations"></a>如何修正違規
 請檢查命令式安全性需求，確保許可權的狀態不依賴在使用許可權時可能變更的資訊。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果許可權不依賴變更的資料，則可以安全地隱藏此規則的警告。 不過，最好將命令式需求變更為其宣告式對應項。

## <a name="see-also"></a>請參閱
 [安全程式碼撰寫方針](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)[資料與模型](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)化
