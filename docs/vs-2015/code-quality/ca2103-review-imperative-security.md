---
title: Ca2103： 必須檢閱命令式安全性 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: dd075c4c6edc84422c6c09846d23ef0049d55002
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886548"
---
# <a name="ca2103-review-imperative-security"></a>CA2103：必須檢視命令式安全性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法會使用命令式安全性，而且可能會利用只要要求正在使用中就可能變更的狀態資訊或傳回值建構權限。

## <a name="rule-description"></a>規則描述
 命令式安全性會使用受管理的物件，指定在程式碼執行時，相較於使用屬性來儲存中繼資料中的權限和動作中的宣告式安全性的權限和安全性動作。 命令式安全性是非常大的彈性，因為您可以設定權限物件的狀態，並選取使用不到執行階段資訊的安全性動作。 一起彈性會伴隨的執行階段資訊，您用來判斷權限的狀態不會保持不變，只要的動作是 作用中的風險。

 請盡可能使用宣告式安全性。 宣告式要求較容易了解。

## <a name="how-to-fix-violations"></a>如何修正違規
 檢閱命令式安全性要求，藉此確定權限的狀態不會依賴只要正在使用的權限可以變更的資訊。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告，如果權限不需要變更資料。 不過，最好是命令式的要求變更為相等的宣告式。

## <a name="see-also"></a>另請參閱
 [安全程式碼撰寫指導方針](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)[資料與模型化](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



