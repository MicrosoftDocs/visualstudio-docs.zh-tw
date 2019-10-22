---
title: CA1713：事件的前面或後面不應該有前置詞 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7286272e121cf5054013576c4278f787c8423d79
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669157"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713：事件不應有 before 或 after 前置字元
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|Category|Microsoft. 命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 事件的名稱開頭為 ' Before ' 或 ' After '。

## <a name="rule-description"></a>規則描述
 事件名稱應該會描述引發事件的動作。 若要命名在特定序列 (Sequence) 中引發的相關事件，請使用現在式或過去式表示動作序列相對的位置。 例如，當命名一組在關閉資源時所引發的事件時，您可以將它命名為 ' Closed ' 和 ' 封閉式 '，而不是 ' BeforeClose ' 和 ' AfterClose '。

 命名慣例提供以通用語言執行時間為目標之程式庫的常見外觀。 這可減少新軟體程式庫所需的學習曲線，並提高客戶對於開發 managed 程式碼專業知識的人員所開發的信心。

## <a name="how-to-fix-violations"></a>如何修正違規
 移除事件名稱中的前置詞，並考慮將名稱變更為使用動詞的目前或過去的時態。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。
