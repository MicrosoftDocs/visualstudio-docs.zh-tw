---
title: "如何： 使用匯入設計工具 |Microsoft 文件"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3980b43b090a0a6321ee0133e2c0ad4f5cbbffde
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-use-the-imports-designer"></a>HOW TO：使用匯入設計工具
匯入設計工具可讓您輸入要用於運算式之型別的命名空間。 就像是**匯入**或**使用**Visual Basic 和 C# 中，匯入設計工具中指定命名空間中的關鍵字可讓您只要在您的運算式，而非完整輸入型別名稱型別名稱。  
  
 匯入設計工具皆可與 UI 變更和儲存工作流程時所做的變更互動。 儲存工作流程時，會自動將命名空間加入匯入設計工具。 這些需求包括下列各項：  
  
-   用於變數與引數宣告之任何型別的命名空間。  
  
-   用於運算式之任何型別的命名空間。  
  
-   用於序列化工作流程的任何其他命名空間 (例如，置放於工作流程之自訂活動所使用的命名空間)。  
  
 儲存工作流程時，您可能會注意到，因為前一個清單所描述的邏輯，某些手動刪除的命名空間會自動重新加入至匯入設計工具。  
  
### <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>若要將命名空間加入至匯入命名空間的清單  
  
1.  開啟 WCF 工作流程服務應用程式、工作流程主控台應用程式、[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] 中的活動程式庫專案，或重新裝載的工作流程應用程式。  
  
2.  按一下**匯入**主畫布底部。 隨即出現匯入設計工具。  
  
3.  輸入命名空間，或從匯入設計工具上方的下拉式清單控制項中選取命名空間。  
  
     輸入時，會出現符合型別字元的有效命名空間清單。  
  
4.  按**Enter**將命名空間新增至清單。  
  
5.  如果您想要從清單中移除命名空間中，選取的命名空間，然後按**刪除**鍵盤上的索引鍵。 請注意命名空間只有在因任何理由無效時才能加以刪除，例如專案不再參考包含該命名空間的組件。