---
title: 安裝協力廠商單元測試架構 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 47893b70-46f8-49dc-84bd-ec820178f683
caps.latest.revision: 12
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7ae69e33d60c4d6bc4257c6c9006b795d8cbdced
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "57868703"
---
# <a name="install-third-party-unit-test-frameworks"></a>安裝協力廠商單元測試架構
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 測試總管可以執行任何已針對總管開發配接器介面的單元測試架構。 架構的安裝程式會安裝二進位檔，並加入支援語言版本的 Visual Studio 專案範本。 當您使用範本來建立專案時，系統會向測試總管註冊架構。 Visual Studio 方案可包含多個單元測試專案，這些專案使用不同的架構並提供不同的語言版本。 測試總管會全部一起執行。  
  
 **需求**  
  
-   Visual Studio Enterprise、Visual Studio Professional  
  
## <a name="acquiring-third-party-frameworks"></a>取得協力廠商架構  
 您可以下載許多協力廠商單元測試架構，並使用 Visual Studio 擴充功能管理員，或從 MSDN 網站上的 Visual Studio 組件庫進行安裝。 您也可以從其他網站 (例如架構的網站) 下載架構。  
  
### <a name="installing-from-visual-studio"></a>從 Visual Studio 安裝  
  
1. 選擇標準功能表上的 [工具]，然後選擇 [延伸模組和更新]。  
  
2. 依序展開 [線上]、[Visual Studio 組件庫] 和 [工具]。 選擇 [測試]。  
  
3. 瀏覽清單以尋找架構。  
  
4. 選取架構並選擇 [下載]。  
  
   如需詳細資訊，請參閱[尋找及使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)。  
  
### <a name="installing-from-the-web"></a>從 Web 安裝  
 如果您知道對哪個架構感興趣：  
  
1. 開啟 [Visual Studio Marketplace](https://marketplace.visualstudio.com)。  
  
2. 在 [尋找] 方塊中鍵入架構的名稱。  
  
3. 在結果清單中選擇架構，以巡覽至該工具的 [Visual Studio 組件庫] 頁面。  
  
   若要瀏覽架構和其他測試工具的清單：  
  
4. 開啟 [Visual Studio Marketplace](https://marketplace.visualstudio.com)。  
  
5. 選擇 [瀏覽]。  
  
6. 在 [分類] 清單中，展開 [工具] 節點，然後選擇 [測試]。  
  
7. 在結果清單中選擇一個架構，以巡覽至該工具的 [Visual Studio 組件庫] 頁面。  
  
## <a name="see-also"></a>請參閱  
 [對程式碼進行單元測試](../test/unit-test-your-code.md)
