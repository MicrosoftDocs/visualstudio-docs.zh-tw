---
title: CA1713:事件不應該有 before 或 after 前置字元
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8dba144740a2a39494323a456cddf90131e35c6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920323"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713:事件不應該有 before 或 after 前置字元

|||
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 事件名稱開頭 'Before' 或 'After'。

## <a name="rule-description"></a>規則描述
 事件名稱應該要描述引發事件的動作。 若要命名在特定序列 (Sequence) 中引發的相關事件，請使用現在式或過去式表示動作序列相對的位置。 比方說，當命名一組事件引發時關閉資源時，您可能會為它命名 '關閉' 和 'Closed'，而不是 'BeforeClose' 和 'AfterClose'。

 命名慣例提供了通用程式庫 common language runtime 為目標。 這可降低學習曲線，需要新的軟體程式庫，並增加程式庫，開發人員專業開發的 managed 程式碼中的其他人的客戶信心。

## <a name="how-to-fix-violations"></a>如何修正違規
 移除事件名稱的前置詞，請考慮變更要使用現在式或過去式動詞命令的名稱。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。