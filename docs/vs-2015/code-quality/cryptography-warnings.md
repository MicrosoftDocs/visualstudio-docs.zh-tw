---
title: 密碼編譯警告 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 947721de606cb6117ed2fd5f84bbc51e20e08203
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499777"
---
# <a name="cryptography-warnings"></a>密碼編譯警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[密碼編譯警告](https://docs.microsoft.com/visualstudio/code-quality/cryptography-warnings)。  
  
密碼編譯警告透過正確使用加密來支援更安全的程式庫與應用程式。 這些警告有助於防止在程式中出現安全性問題。 如果停用這些警告中的任一個，則您應該清楚地在程式碼中標示理由，同時也要通知指定的安全主管有關您的開發專案。  
  
|規則|描述|  
|----------|-----------------|  
|[CA5350：請勿使用弱式密碼編譯演算法](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|現今，弱式加密演算法和雜湊函式用於多種原因，但它們不應該用來保證所保護資料的機密性或完整性。        此規則會在它在程式碼中發現 TripleDES、SHA1 或 RIPEMD160 演算法時觸發。|  
|[CA5351 不要使用中斷的密碼編譯演算法](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|中斷的密碼編譯演算法較不安全，強烈建議您不要使用它們。 此規則會在它在程式碼中發現 MD5 雜湊演算法或 DES 或 RC2 加密演算法時觸發。|



