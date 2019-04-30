---
title: HOW TO：使用引數設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 90e259d9d5e71ab5e6837cc4aa9cd22ebf43aaac
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432370"
---
# <a name="how-to-use-the-argument-designer"></a>HOW TO：使用引數設計工具
與舊版 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 相較，引數設計工具可讓資料更容易流入及流出活動。 按一下即可存取設計工具**引數**設計畫布左下角的按鈕。 設計工具會包含一份表格顯示，並可依每個資料行標頭中，除了引數**預設值**資料行。 每個引數都包含名稱、in/out/in-out/屬性方向、型別與預設運算式值 (如果有的話)。 名稱與預設運算式值都是可編輯的文字欄位，而型別和方向都可從下拉式清單中選取。 [!INCLUDE[crabout](../includes/crabout-md.md)] 引數，請參閱[變數和引數](http://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)。  
  
### <a name="to-create-a-new-argument"></a>若要建立新引數  
  
1. 在 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 中開啟工作流程或活動的方案。  
  
2. 開啟 [引數設計工具]，請依序按一下**引數**設計畫布左下角的按鈕。 引數設計工具隨即出現。  
  
3. 按一下標示為空白資料列**建立引數**。 這會將新的資料列新增使用新的引數，使用下列的預設值： 針對 argumentx**名稱**其中 x 是整數，其初始值為 1，會自動遞增以建立唯一的引數名稱**中** for**方向**，和**字串**如**引數型別**。 不加入任何值**預設值**。 在工作流程設計過程中，您隨時可以變更這些值。  
  
    > [!NOTE]
    > 若要刪除引數，選取引數依序按一下它，然後按**刪除**索引鍵。  
  
## <a name="see-also"></a>另請參閱  
 [使用工作流程設計工具](../workflow-designer/using-the-workflow-designer.md)   
 [變數與引數](http://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)