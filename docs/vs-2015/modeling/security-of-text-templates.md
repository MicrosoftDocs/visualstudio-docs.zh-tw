---
title: 文字範本的安全性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f21bfadd540ce365c7f585a35991c27395558c6e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60058652"
---
# <a name="security-of-text-templates"></a>文字範本的安全性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

文字範本具有下列安全性考量：  
  
- 文字範本受到任意程式碼插入。  
  
- 如果主應用程式用來尋找指示詞處理器的機制並不安全，就可以執行惡意的指示詞處理器。  
  
## <a name="arbitrary-code"></a>任意程式碼  
 當您撰寫範本時，您可以將放在任何程式碼\<# # > 標記。 這允許任意程式碼從文字範本內執行。  
  
 請務必從受信任的來源取得的範本。 請確定您的應用程式未執行不是來自信任來源的範本的使用者，即發出警告。  
  
## <a name="malicious-directive-processor"></a>惡意的指示詞處理器  
 文字範本引擎互動轉換主應用程式和一個或多個指示詞處理器，將轉換的輸出檔的範本文字。 如需詳細資訊，請參閱 <<c0> [ 文字範本轉換流程](../modeling/the-text-template-transformation-process.md)。  
  
 如果主應用程式用來尋找指示詞處理器的機制並不安全的會執行惡意的指示詞處理器的風險。 惡意的指示詞處理器無法提供執行中的程式碼`FullTrust`執行範本時的模式。 如果您建立自訂文字範本轉換主應用程式時，您必須使用安全的機制，例如登錄中，找出指示詞處理器引擎。
