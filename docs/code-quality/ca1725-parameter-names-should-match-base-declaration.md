---
title: CA1725:參數名稱應該符合基底類型的宣告
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9135ab768d3439cc996478da31343553902706fa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860594"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725:參數名稱應該符合基底類型的宣告

|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 在外部可見方法的覆寫參數的名稱與基底宣告、 方法或介面宣告的方法中參數的名稱中的參數名稱不相符。

## <a name="rule-description"></a>規則描述
 在覆寫階層架構中一致的參數命名方式，會增加方法覆寫的可用性。 與基底宣告中的名稱不同之衍生方法中的參數名稱，可能會造成方法為基底方法的覆寫或為方法的新多載而混淆。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，重新命名以符合基底宣告的參數。 修正方法是 COM 可見方法的重大變更。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏這項規則，除了先前所提供的程式庫中的 COM 可見方法的警告。