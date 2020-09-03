---
title: CA2207：初始化實數值型別的靜態欄位 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 792fe18a4f472d0b8a4fd62c652f2ae34fcf6864
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546298"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207:必須將實值類型的靜態欄位內嵌初始化
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|類別|Microsoft. 使用量|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 實值型別會宣告明確的靜態函式。

## <a name="rule-description"></a>規則描述
 宣告實值型別時，它會進行預設初始化，其中所有的實值型別字段都設定為零，而且所有的參考型別字段都設定為 `null` `Nothing` Visual Basic) 中的 (。 明確靜態的函式只保證在呼叫類型的實例的函式或靜態成員之前執行。 因此，如果在不呼叫實例的函式的情況下建立類型，則不保證會執行靜態的函式。

 如果所有靜態資料都是以內嵌方式初始化，但未宣告明確的靜態函式，則 c # 和 Visual Basic 編譯器會在 `beforefieldinit` MSIL 類別定義中加入旗標。 編譯器也會加入包含靜態初始化程式碼的私用靜態函式。 此私用靜態函式保證會在存取類型的任何靜態欄位之前執行。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請在宣告所有靜態資料時將其初始化，並移除靜態的函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="related-rules"></a>相關規則
 [CA1810:必須將參考類型內部的靜態欄位初始化](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)
