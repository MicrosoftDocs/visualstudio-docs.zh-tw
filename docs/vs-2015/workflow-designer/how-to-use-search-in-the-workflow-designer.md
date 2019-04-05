---
title: HOW TO：使用 [搜尋]，請在工作流程設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 427e854c19e65463abcd8780cfe95d38f3ea66f4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943949"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>HOW TO：使用工作流程設計工具中的搜尋
為了方便建立更大型且更為複雜的工作流程，可以在工作流程設計工具中使用「搜尋」，依關鍵字來尋找項目。 請注意，設計工具不支援「取代」。 「搜尋」可在設計工具中尋找下列項目：  
  
## <a name="quick-find"></a>快速尋找  
 「快速尋找」可在設計工具中尋找下列項目：  
  
-   <xref:System.Activities.Activity> 物件、<xref:System.Activities.Statements.FlowNode> 物件、<xref:System.Activities.Statements.State> 物件、轉換及其他自訂流程控制項目的屬性。  
  
-   變數  
  
-   引數  
  
-   運算式  
  
#### <a name="using-quick-find"></a>使用快速尋找  
  
1.  工作流程設計工具中開啟，然後按**Ctrl + F**，或選取**編輯**，**尋找及取代**，**快速尋找**。  
  
2.  輸入搜尋詞彙**Find what**文字方塊中，按一下 **尋找下一個**。  
  
3.  系統會在目前工作流程中尋找搜尋字詞。 下列螢幕擷取畫面顯示目前在設計工具中找到的活動顯示名稱。  
  
     ![在工作流程設計工具中搜尋結果](../workflow-designer/media/designersearch.png "DesignerSearch")  
  
## <a name="find-in-files"></a>檔案中尋找  
 使用「檔案中尋找」將在工作流程檔案 (包含 XAML 檔案) 中尋找字串。  
  
#### <a name="using-find-in-files"></a>使用檔案中尋找  
  
1.  在 Visual Studio 中按**Ctrl + Shift + F**，或選取**編輯**，**尋找及取代**，**檔案中尋找**  
  
2.  輸入搜尋項目插入**Find what**文字方塊中，按一下 **全部尋找**  
  
3.  尋找結果將會顯示在[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]**尋找結果**檢視。 按兩下結果項目會巡覽至工作流程設計工具中包含相符項目的活動。