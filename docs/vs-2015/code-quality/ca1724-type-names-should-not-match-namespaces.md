---
title: CA1724： 類型名稱不應該符合命名空間 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5028646e5c937caad60a35e67ab9935a5755929a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588056"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724：類型名稱不應該和命名空間相符
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA1724： 類型名稱應該不相符項目命名空間](https://docs.microsoft.com/visualstudio/code-quality/ca1724-type-names-should-not-match-namespaces)。

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類型名稱符合[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]不區分大小寫的比較中的命名空間名稱。

## <a name="rule-description"></a>規則描述
 類型名稱不得符合 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Class Library 中定義的命名空間名稱。 違反此規則會降低程式庫的可用性。

## <a name="how-to-fix-violations"></a>如何修正違規
 選取名稱不相符的型別名稱[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]類別程式庫命名空間。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 新的開發，沒有已知的情況下會發生您必須在其中隱藏此規則的警告。 隱藏警告之前，請仔細考慮如何將程式庫的使用者可能會比對名稱所混淆。 針對隨附的程式庫，您可能必須隱藏此規則的警告。



