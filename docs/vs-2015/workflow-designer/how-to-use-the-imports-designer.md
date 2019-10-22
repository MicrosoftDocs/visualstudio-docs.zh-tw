---
title: 如何：使用匯入設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 47b5055cca0b00e7fdec49947df13b473a090aaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659088"
---
# <a name="how-to-use-the-imports-designer"></a>HOW TO：使用匯入設計工具
匯入設計工具可讓您輸入要用於運算式之型別的命名空間。 就像是在 Visual Basic .net 和C#中的匯**入**或使用關鍵字，在 [匯入設計工具] 中指定命名空間，可讓您只在運算式中輸入型別名稱，而不是完整的版本類型名稱。

 匯入設計工具皆可與 UI 變更和儲存工作流程時所做的變更互動。 儲存工作流程時，會自動將命名空間加入匯入設計工具。 這些需求包括下列各項：

- 用於變數與引數宣告之任何型別的命名空間。

- 用於運算式之任何型別的命名空間。

- 用於序列化工作流程的任何其他命名空間 (例如，置放於工作流程之自訂活動所使用的命名空間)。

  儲存工作流程時，您可能會注意到，因為前一個清單所描述的邏輯，某些手動刪除的命名空間會自動重新加入至匯入設計工具。

### <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>若要將命名空間加入至匯入命名空間的清單

1. 開啟 WCF 工作流程服務應用程式、工作流程主控台應用程式、[!INCLUDE[vs2010](../includes/vs2010-md.md)] 中的活動程式庫專案，或重新裝載的工作流程應用程式。

2. 按一下主畫布底部的 [匯**入**]。 隨即出現匯入設計工具。

3. 輸入命名空間，或從匯入設計工具上方的下拉式清單控制項中選取命名空間。

     輸入時，會出現符合型別字元的有效命名空間清單。

4. 按**enter**鍵，將命名空間新增至清單。

5. 如果您想要從清單中移除命名空間，請選取命名空間，然後按鍵盤上的**Delete**鍵。 請注意命名空間只有在因任何理由無效時才能加以刪除，例如專案不再參考包含該命名空間的組件。