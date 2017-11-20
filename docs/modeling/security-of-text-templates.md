---
title: "文字範本的安全性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, security
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: "23"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 7c99f0a519ec62a2b9946baba072b0256a78697a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
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