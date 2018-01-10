---
title: "分析組建驗證測試中的程式碼涵蓋範圍 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 3f02166c89837dfd122ab8a8c71913c659ab1dd2
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2018
---
# <a name="analyzing-code-coverage-in-build-verification-tests"></a>分析組建驗證測試中的程式碼涵蓋範圍
在 Microsoft Visual Studio 的程式碼涵蓋範圍分析顯示您有多少程式碼由自動化的測試執行。 如需詳細資訊，請參閱[使用程式碼涵蓋範圍來決定所測試的程式碼數量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)。  
  
 當您檢查程式碼時，您的測試會在組建伺服器上與其他小組成員的所有其他測試一起執行。 (如果您尚未設定此功能，請參閱[在建置流程中執行測試](http://msdn.microsoft.com/Library/d05743a1-c5cf-447e-bed9-bed3cb595e38)。)由於分析組建服務的程式碼涵蓋範圍可以針對整個專案的涵蓋範圍提供最新、最完整的分析結果，因此是非常有用的方法。 這項分析也包含自動化系統測試，和通常不會在開發電腦上執行的其他自動程式碼測試。  
  
1.  在 Team Explorer 中開啟 [組建]，然後新增或編輯組建定義。  
  
2.  在 [流程] 頁面上，展開 [自動化測試]、[測試來源]、[回合設定]。 將 [回合設定檔的類型] 設為 [已啟用程式碼涵蓋範圍]。  
  
     如果您有一個以上的測試來源定義，請針對每一個定義重複以上步驟。  
  
    -   但沒有名為 [回合設定檔類型]** 的欄位。  
  
         在 [自動化測試] 下，選取 [測試組件]，然後選擇行末的省略符號按鈕 [...]。 在 [加入/編輯測試回合] 對話方塊中，選擇 [測試執行器] 之下的 [Visual Studio 測試執行器]。  
  
 ![設定程式碼涵蓋範圍的組建定義](../test/media/codecoverage-plaincc.png "CodeCoverage-plainCC")  
  
 組建執行之後，程式碼涵蓋範圍結果會顯示在組建摘要中。  
  
## <a name="see-also"></a>請參閱  
 [使用程式碼涵蓋範圍來決定所測試的程式碼數量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
