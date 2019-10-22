---
title: CA1725：參數名稱應該符合基底宣告 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 128069bb24dfc8b1c11963e33c9541701b0eea15
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653745"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725：參數名稱應該符合基底宣告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Category|Microsoft. 命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見方法覆寫中的參數名稱，與方法之基底宣告中的參數名稱或方法的介面宣告中的參數名稱不相符。

## <a name="rule-description"></a>規則描述
 在覆寫階層架構中一致的參數命名方式，會增加方法覆寫的可用性。 與基底宣告中的名稱不同之衍生方法中的參數名稱，可能會造成方法為基底方法的覆寫或為方法的新多載而混淆。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請重新具名引數以符合基底宣告。 修正是 COM 可見方法的重大變更。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 除了先前隨附的程式庫中的 COM 可見方法以外，請勿隱藏此規則的警告。
