---
title: CA2103:必須檢閱命令式安全性
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ae092017890552613bfddb16cf0c7313cf422e5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54967241"
---
# <a name="ca2103-review-imperative-security"></a>CA2103:必須檢閱命令式安全性

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

- [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)
- [資料與模型化](/dotnet/framework/data/index)