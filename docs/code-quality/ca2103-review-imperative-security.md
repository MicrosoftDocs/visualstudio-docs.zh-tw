---
title: CA2103：必須檢視命令式安全性
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a20dc939b305e3ec917f57bcd9f7cc8f8aa735f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914903"
---
# <a name="ca2103-review-imperative-security"></a>CA2103：必須檢視命令式安全性
|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法會使用命令式安全性，而且可能會利用只要要求正在使用中就可能變更的狀態資訊或傳回值建構權限。

## <a name="rule-description"></a>規則描述
 命令式安全性會使用受管理的物件指定的權限和安全性動作程式碼在執行期間，相較於使用屬性來儲存中繼資料中的權限和動作中的宣告式安全性。 命令式安全性相當富彈性，因為您可以設定權限物件的狀態，並選取安全性動作會使用不到執行階段的資訊。 一起彈性會伴隨的執行階段資訊您用來判斷權限的狀態無法維持不變，只要的動作是作用中的風險。

 請盡可能使用宣告式安全性。 宣告式要求較容易了解。

## <a name="how-to-fix-violations"></a>如何修正違規
 檢閱命令式安全性要求，並確定權限的狀態不會依賴只要正在使用的權限可以變更的資訊。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可以安全地隱藏此規則的警告，如果權限不需要變更資料。 不過，最好命令式要求變更為相等的宣告式。

## <a name="see-also"></a>另請參閱
 [安全編碼方針](/dotnet/standard/security/secure-coding-guidelines)[資料與模型化](/dotnet/framework/data/index)