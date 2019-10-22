---
title: 文字範本的安全性
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eab987d406d6a2c05c8350aaac9dd1ecfc13e4a8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660081"
---
# <a name="security-of-text-templates"></a>文字範本的安全性
文字模板具有下列安全性考慮：

- 文字模板容易受到任意程式碼插入的攻擊。

- 如果主機用來尋找指示詞處理器的機制並不安全，則可能會執行惡意的指示詞處理器。

## <a name="arbitrary-code"></a>任意程式碼
 當您撰寫範本時，您可以將任何程式碼放在 \< # # > 標記中。 這可讓您從文字模板內執行任意程式碼。

 請務必從信任的來源取得範本。 請務必警告應用程式的使用者不會執行不是來自受信任來源的範本。

## <a name="malicious-directive-processor"></a>惡意指示詞處理器
 文字模板引擎會與轉換主機互動，以及一或多個指示詞處理器，將範本文字轉換成輸出檔案。 如需詳細資訊，請參閱[文字模板轉換](../modeling/the-text-template-transformation-process.md)程式。

 如果主機用來尋找指示詞處理器的機制並不安全，就會造成執行惡意指示詞處理器的風險。 惡意指示詞處理器可以提供在執行範本時，以 `FullTrust` 模式執行的程式碼。 如果您建立自訂文字模板轉換主機，則必須使用安全的機制（例如登錄），引擎才能找到指示詞處理器。