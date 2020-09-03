---
title: CA2103：檢查命令式安全性 |Microsoft Docs
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
ms.openlocfilehash: ade0d10e203752c7412929c6f5f44d9cbfaacfa6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521260"
---
# <a name="ca2103-review-imperative-security"></a>CA2103:必須檢閱命令式安全性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法會使用命令式安全性，而且可能會利用只要要求正在使用中就可能變更的狀態資訊或傳回值建構權限。

## <a name="rule-description"></a>規則描述
 命令式安全性使用 managed 物件來指定程式碼執行期間的許可權和安全性動作（相較于宣告式安全性），其使用屬性在中繼資料中儲存許可權和動作。 命令式安全性相當有彈性，因為您可以設定權限物件的狀態，並使用在執行時間之前無法使用的資訊來選取安全性動作。 有了這種彈性，您用來判斷許可權狀態的執行時間資訊，只要動作生效，就不會維持不變的風險。

 請盡可能使用宣告式安全性。 宣告式要求更容易瞭解。

## <a name="how-to-fix-violations"></a>如何修正違規
 請參閱命令式安全性需求，確定許可權的狀態不會依賴可能變更的資訊，只要使用了許可權即可。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果許可權不依賴變更資料，則可以安全地隱藏此規則的警告。 不過，最好是將命令式需求變更為它的宣告式對等專案。

## <a name="see-also"></a>另請參閱
 [安全程式碼撰寫指導方針](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)[資料和模型](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
