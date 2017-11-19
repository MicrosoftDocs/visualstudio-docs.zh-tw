---
title: "變更 DataContext 方法的傳回型別無法復原 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 28398032eb4c17916af4294e5ccab386040cf98e
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>如果變更 DataContext 方法的傳回型別，將無法復原
變更 DataContext 方法的傳回型別將無法復原。 若要還原成自動產生的型別，請再次從 [伺服器總管]/[資料庫總管] 將此項目拖曳到 O/R 設計工具上。 您確定要變更此傳回型別嗎?  
  
<xref:System.Data.Linq.DataContext> 方法的傳回型別會根據項目置放在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中的位置而不同。 如果將項目直接放入現有的實體類別，則會建立具有實體類別之傳回型別的 <xref:System.Data.Linq.DataContext> 方法。 如果您將項目放入 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的空白區域，則建立的 <xref:System.Data.Linq.DataContext> 方法會傳回自動產生的型別。 您可以在將 <xref:System.Data.Linq.DataContext> 方法加入至方法窗格後，變更方法的傳回型別。 若要檢查或變更的傳回型別<xref:System.Data.Linq.DataContext>方法中，選取它，然後按一下 **傳回型別**屬性**屬性**視窗。  
  
### <a name="to-change-the-return-type-of-a-datacontext"></a>若要變更 DataContext 的傳回型別  
  
-   按一下 [ **是**]。  
  
### <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>若要結束訊息方塊而不變更傳回型別  
  
-   按一下 [否] 。  
  
### <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>若要在變更傳回型別之後還原成原始傳回型別  
  
1.  選取<xref:System.Data.Linq.DataContext>方法[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]並將它刪除。  
  
2.  找出中的項目**伺服器總管/資料庫總管**並拖曳至[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。  
  
    會建立具有原始預設傳回型別的 <xref:System.Data.Linq.DataContext> 方法。  
  
## <a name="see-also"></a>請參閱
[O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)