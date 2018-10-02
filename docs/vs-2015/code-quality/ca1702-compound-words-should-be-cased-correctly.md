---
title: CA1702： 複合字應該使用的大小寫正確 |Microsoft Docs
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
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c9a5e532391937963108d405178571d02687d1af
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487204"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702：複合字應該使用正確的大小寫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 2017 的最新文件，請參閱 < [CA1702： 複合字應該使用正確的大小寫](https://docs.microsoft.com/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly)docs.microsoft.com 上。  
  
|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|分類|Microsoft.Naming|  
|中斷變更|組件中斷時引發。<br /><br /> 非-中斷-引發時的類型參數。|  
  
## <a name="cause"></a>原因  
 識別項的名稱包含多個字組，並至少其中一個字似乎是大小寫不正確的複合字。  
  
## <a name="rule-description"></a>規則描述  
 識別項的名稱會分割成文字為基礎的大小寫。 每個連續的兩個字組合會檢查 Microsoft 拼字檢查程式庫。 如果辨識出它是，識別項會產生規則的違規情形。 造成違規的複合字的範例是"CheckSum"和"MultiPart 」，這應該使用的大小寫為"Checksum"和"Multipart"，分別。 因為前一個常見的用法，幾個例外狀況內建規則，以及數個單字會加上旗標，例如"工具列"和"Filename"，，應該使用的大小寫成兩個不同的單字 （在此情況下，在"工具列"和"FileName"）。  
  
 命名慣例提供了通用程式庫 common language runtime 為目標。 這可降低學習曲線，需要新的軟體程式庫，並增加程式庫，開發人員專業開發的 managed 程式碼中的其他人的客戶信心。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 是正確的大小寫，請變更名稱。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可安全地隱藏此規則的警告，如果拼字檢查字典所辨識的複合字的兩個部分，且其目的是要使用兩個字。  
  
## <a name="related-rules"></a>相關的規則  
 [CA1701：資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>另請參閱  
 [命名方針](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)   
 [大小寫慣例](http://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)

