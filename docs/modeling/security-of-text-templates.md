---
title: 文字範本的安全性
description: 深入瞭解安全性和文字模板，包括任意程式碼和惡意指示詞處理器等主題。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a740a6f7a4c532a61a5e412c94fa4321c5da707
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385756"
---
# <a name="security-of-text-templates"></a>文字範本的安全性
文字模板有下列安全性考慮：

- 文字模板易受限於任意程式碼插入。

- 如果主機用來尋找指示詞處理器的機制並不安全，則可能會執行惡意指示詞處理器。

## <a name="arbitrary-code"></a>任意程式碼
 當您撰寫範本時，您可以在標記內放置任何程式碼 \<# #> 。 這可讓您從文字模板內執行任意程式碼。

 請務必從信任的來源取得範本。 請務必警告您應用程式的使用者不會執行不是來自受信任來源的範本。

## <a name="malicious-directive-processor"></a>惡意指示詞處理器
 文字模板引擎會與轉換主機互動，以及一或多個指示詞處理器，以將範本文字轉換成輸出檔。 如需詳細資訊，請參閱 [文字模板轉換流程](../modeling/the-text-template-transformation-process.md)。

 如果主機用來尋找指示詞處理器的機制並不安全，它就會執行惡意指示詞處理器的風險。 惡意指示詞處理器可以提供在執行範本時以模式執行的程式碼 `FullTrust` 。 如果您建立自訂文字模板轉換主機，則必須使用安全機制（例如登錄），引擎才能找出指示詞處理器。
