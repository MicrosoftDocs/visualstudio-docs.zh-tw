---
title: CA1061： 不要隱藏基底類別方法 |Microsoft Docs
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
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8bcee9f4bee5f5e505b4dddfb53d6a4cf30c39c0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826722"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061：不要隱藏基底類別方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 衍生的型別宣告具有相同名稱和相同數目的參數做為其基底方法，其中一個方法一或多個參數是在基底方法; 中的對應參數的基底類型而且任何剩餘的參數具有相同基底方法中的對應參數的類型。

## <a name="rule-description"></a>規則描述
 在衍生方法的參數簽章只有不同的類型還要弱衍生比基底方法的參數簽章中對應的類型時所衍生的型別中的相同具名方法隱藏基底類型中的方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除或重新命名方法，或變更的參數簽章，使方法不會隱藏基底方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會示範違反規則的方法。

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.HideBaseMethod/cs/FxCop.Design.HideBaseMethod.cs#1)]



