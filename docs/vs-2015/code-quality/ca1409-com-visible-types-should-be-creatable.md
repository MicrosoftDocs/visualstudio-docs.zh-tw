---
title: 'CA1409: Com 可見類型應該是可建立 |Microsoft Docs'
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
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2aa50d16f0661b3c4baa40fae24fbee24f6fa7bd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200313"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409：COM 可見類型應該是可建立的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|分類|Microsoft.Interoperability|
|中斷變更|非重大|

## <a name="cause"></a>原因
 特別標示為可見的元件物件模型 (COM) 參考型別包含公用參數化建構函式，但不包含公用預設 （無參數） 建構函式。

## <a name="rule-description"></a>規則描述
 COM 用戶端無法建立沒有公用預設建構函式的類型。 不過，類型可以仍可存取由 COM 用戶端如果另一個方法可建立類型，並將它傳遞給用戶端 （例如，透過方法呼叫的傳回值）。

 此規則會忽略型別衍生自<xref:System.Delegate?displayProperty=fullName>。

 根據預設，以下是為 COM 所見： 組件、 公用型別、 公用的型別中的公用執行個體成員和公用實值型別的所有成員。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入公用預設建構函式，或移除<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>從型別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它是安全地隱藏此規則的警告，如果提供的其他方式建立，並將物件傳遞給 COM 用戶端。

## <a name="related-rules"></a>相關的規則
 [CA1017：組件必須標記 ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>另請參閱
 [限定互通的.NET 類型](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)[與相互操作 Unmanaged 程式碼](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



