---
title: CA1716:識別項不應該和關鍵字相符 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 35a97e62e17895cb700a1420c7851878f329112a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941142"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716:識別項名稱不應該和關鍵字相符
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 命名空間、 類型或 viritual 或介面成員的名稱符合保留的關鍵字，以程式設計的語言。

## <a name="rule-description"></a>規則描述
 命名空間、 類型識別項和虛擬和介面成員不應該符合 common language runtime 為目標的語言所定義的關鍵字。 根據所使用的語言和關鍵字，編譯器錯誤和模稜兩可會讓程式庫難以使用。

 此規則會檢查針對下列語言版本的關鍵字：

- Visual Basic

- C#

- C++/CLI

  不區分大小寫的比較來[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]關鍵字和區分大小寫比較，用於其他語言。

## <a name="how-to-fix-violations"></a>如何修正違規
 名稱，不會出現在清單中選取的關鍵字。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您說服識別碼不會混淆的 API，使用者和程式庫是使用中的所有可用語言，您可以隱藏此規則的警告[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]。
