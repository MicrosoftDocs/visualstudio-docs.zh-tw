---
title: CA1020:避免一些類型，在命名空間 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8c94cf09b43eb09482be4a30d9f0b9206678c4dc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435837"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020:避免在命名空間中包含過少的類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 全域命名空間以外的命名空間包含少於五個的型別。

## <a name="rule-description"></a>規則描述
 確定命名空間的每個都有邏輯組織，並將存在合理的理由稀疏填入的命名空間中的類型。 命名空間應該包含在大部分情況下一起使用的類型。 互斥他們的應用程式時，類型應該位於個別的命名空間。 比方說，<xref:System.Web.UI>命名空間包含型別，用於 Web 應用程式，而<xref:System.Windows.Forms>命名空間包含類型中所使用的[!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)]-應用程式。 即使兩個命名空間的控制層面的使用者介面的類型，這些型別並非設計在相同的應用程式中使用。 因此，它們位於不同的命名空間中。 因為這會增加一項功能的可搜尋性，小心命名空間的組織可以也很有用。 藉由檢查命名空間階層，程式庫取用者應該能夠找到型別會實作功能。

> [!NOTE]
> 設計階段型別和權限應該不會合併到其他的命名空間，以符合這項指導方針。 這些型別屬於自己的命名空間，以下主要命名空間，而且命名空間應該結尾`.Design`和`.Permissions`分別。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請嘗試結合成單一的命名空間包含少數類型的命名空間。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告，命名空間不包含其他的命名空間中的型別搭配使用的類型時。
