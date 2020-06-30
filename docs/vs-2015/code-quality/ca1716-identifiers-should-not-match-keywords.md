---
title: CA1716：識別碼不應符合關鍵字 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 67a3588a857a0eea7d338217f975ed593dfdad52
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543698"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716:識別項名稱不應該和關鍵字相符
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|類別|Microsoft. 命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 命名空間、類型或 viritual 或介面成員的名稱，會符合程式語言中的保留關鍵字。

## <a name="rule-description"></a>規則描述
 命名空間、類型和虛擬和介面成員的識別碼，不應符合以 common language runtime 為目標之語言所定義的關鍵字。 視所使用的語言和關鍵字而定，編譯器錯誤和多義性可能會使程式庫變得很容易使用。

 此規則會針對下列語言的關鍵字進行檢查：

- Visual Basic

- C#

- C++/CLI

  關鍵字會使用不區分大小寫的比較 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ，而其他語言會使用區分大小寫比較。

## <a name="how-to-fix-violations"></a>如何修正違規
 選取不會出現在關鍵字清單中的名稱。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您確信該識別碼不會混淆 API 的使用者，而且該程式庫可用於中的所有可用語言，您可以隱藏此規則的警告 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。
