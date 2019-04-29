---
title: CA1724:類型名稱不應該和命名空間相符
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f81327324de937df57edfb36cae34d613f6298a5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546016"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724:類型名稱不應該和命名空間相符

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因

型別名稱比對一或多個外部可見的類型參考的命名空間名稱。 名稱比較不區分大小寫。

## <a name="rule-description"></a>規則描述

使用者建立的型別名稱應該不相符參考具有外部可見類型的命名空間的名稱。 違反此規則可能會降低您的程式庫的可用性。

## <a name="how-to-fix-violations"></a>如何修正違規

重新命名此類型，使它不符合為具有外部可見類型的參考命名空間的名稱。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

新的開發，沒有已知的情況下會發生您必須在其中隱藏此規則的警告。 隱藏警告之前，請仔細考慮如何將程式庫的使用者可能會比對名稱所混淆。 針對隨附的程式庫，您可能必須隱藏此規則的警告。