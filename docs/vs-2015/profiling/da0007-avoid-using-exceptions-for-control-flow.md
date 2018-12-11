---
title: DA0007：避免使用例外狀況控制流程 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a86c36c55d11f91daff8e876e852daed2f222307
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737090"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007：避免使用例外狀況進行控制流程
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

規則 Id |DA0007 |  
|類別目錄 |.NET Framework 使用方式 |  
|程式碼剖析方法 |所有 |  
|訊息 |會一致地擲回大量例外狀況。 請考慮減少使用中程式邏輯的例外狀況。 |  
|訊息類型 |警告 |  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 25 個樣本才能觸發此規則。  
  
## <a name="cause"></a>原因  
 在分析資料中呼叫高比率的 .NET Framework 例外處理常式。 請考慮使用其他控制流程邏輯，以減少擲回的例外狀況數量。  
  
## <a name="rule-description"></a>規則描述  
 雖然使用例外處理常式來攔截中斷程式執行的錯誤和其他事件是一個好方法，但是在一般的程式執行邏輯中使用例外處理常式可能會很耗費資源，應予以避免。 在大部分情況下，最好只針對很少發生且未預期的情況使用例外狀況。 例外狀況不應該用來當做一般程式流程的一部分傳回值。 在許多情況下，您可以驗證值並使用條件式邏輯以暫止執行導致問題的陳述式，來避免引發例外狀況。  
  
 如需詳細資訊，請參閱 MSDN 上 **Microsoft Patterns and Practices** 文件庫中＜改進 .NET 應用程式效能和延展性＞(英文) 的＜第 5 章 - 改進 Managed 程式碼的效能＞(英文) 中的[例外狀況管理 (英文)](http://go.microsoft.com/fwlink/?LinkID=177825) 一節。  
  
## <a name="how-to-investigate-a-warning"></a>如何調查警告  
 按兩下 [錯誤清單] 視窗中的訊息，瀏覽至 [標記] 檢視。 尋找包含 **.NET CLR Exceptions(@ProcessInstance)\\# of Exceps Thrown / sec** 度量的欄位。 判斷是否有特定的程式執行階段，當中的例外狀況處理比其他階段更頻繁。 使用取樣設定檔，嘗試識別 throw 陳述式以及產生頻繁例外狀況的 try/catch 區塊。 如果有必要，請在 catch 區塊中加入邏輯，協助您了解最常處理的例外狀況。 如果可行，請將經常執行的 throw 陳述式或 catch 區塊，取代為簡單的流程控制邏輯或驗證程式碼。  
  
 例如，如果您發現應用程式經常處理 DivideByZeroException 例外狀況，在程式中加入邏輯來檢查分母是否有零值將可改善應用程式的效能。



