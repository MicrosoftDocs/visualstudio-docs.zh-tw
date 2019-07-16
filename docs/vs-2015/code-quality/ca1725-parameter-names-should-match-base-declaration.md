---
title: CA1725:參數名稱應該符合基底宣告 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e97431b46640fb8241d6bde80d09d38084650be8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143178"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725:參數名稱應該符合基底類型的宣告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
