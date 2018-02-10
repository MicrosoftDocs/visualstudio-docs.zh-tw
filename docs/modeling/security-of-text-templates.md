---
title: "文字範本的安全性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5c6b8d64e02562887b2bc438943fdfe7be3b2e1c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="security-of-text-templates"></a>文字範本的安全性
文字範本具有下列安全性考量：  
  
-   文字範本受到任意程式碼插入。  
  
-   如果主機用來尋找指示詞處理器的機制並不安全，就無法執行惡意的指示詞處理器。  
  
## <a name="arbitrary-code"></a>任意程式碼  
 當您撰寫範本時，您可以將任何程式碼內\<# # > 標記。 這可讓從文字範本內執行的任意程式碼。  
  
 請務必從受信任的來源取得的範本。 請確定您的應用程式未執行不是來自信任來源的範本的使用者，即發出警告。  
  
## <a name="malicious-directive-processor"></a>惡意的指示詞處理器  
 文字範本引擎互動轉換主應用程式和一個或多個指示詞處理器轉換的輸出檔的範本文字。 如需詳細資訊，請參閱[文字範本轉換流程](../modeling/the-text-template-transformation-process.md)。  
  
 如果主應用程式用來尋找指示詞處理器的機制並不安全的它會執行執行惡意的指示詞處理器的風險。 惡意的指示詞處理器無法提供執行中的程式碼`FullTrust`模式執行的範本時。 如果您建立自訂文字範本轉換主應用程式，您必須使用的安全機制，例如登錄中，尋找指示詞處理器引擎。