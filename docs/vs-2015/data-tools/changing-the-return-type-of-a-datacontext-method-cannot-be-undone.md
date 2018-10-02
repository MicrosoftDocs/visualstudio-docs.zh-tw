---
title: 變更 DataContext 方法的傳回型別無法復原 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2adc93f6426c39d26395bdeb88fb8c37112a1a98
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498126"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>如果變更 DataContext 方法的傳回型別，將無法復原
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[變更 DataContext 方法的傳回型別無法復原](https://docs.microsoft.com/visualstudio/data-tools/changing-the-return-type-of-a-datacontext-method-cannot-be-undone)。  
  
  
變更 DataContext 方法的傳回型別將無法復原。 若要還原成自動產生的型別，請再次從 [伺服器總管]/[資料庫總管] 將此項目拖曳到 O/R 設計工具上。 您確定要變更此傳回型別嗎?  
  
 <xref:System.Data.Linq.DataContext> 方法的傳回型別會根據項目置放在 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]中的位置而不同。 如果將項目直接放入現有的實體類別，則會建立具有實體類別之傳回型別的 <xref:System.Data.Linq.DataContext> 方法。 如果您將項目放入 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]的空白區域，則建立的 <xref:System.Data.Linq.DataContext> 方法會傳回自動產生的型別。 您可以在將 <xref:System.Data.Linq.DataContext> 方法加入至方法窗格後，變更方法的傳回型別。 若要檢查或變更的傳回型別<xref:System.Data.Linq.DataContext>方法中，選取它，然後按一下**傳回型別**中的屬性**屬性**視窗。  
  
### <a name="to-change-the-return-type-of-a-datacontext"></a>若要變更 DataContext 的傳回型別  
  
-   按一下 [ **是**]。  
  
### <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>若要結束訊息方塊而不變更傳回型別  
  
-   按一下 [否] 。  
  
### <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>若要在變更傳回型別之後還原成原始傳回型別  
  
1.  選取 <xref:System.Data.Linq.DataContext>方法[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]並將它刪除。  
  
2.  找出中的項目**伺服器總管/資料庫總管**並將它拖曳到[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]。  
  
     會建立具有原始預設傳回型別的 <xref:System.Data.Linq.DataContext> 方法。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)   
 [如何： 建立對應至預存程序和函式 （O/R 設計工具） 的 DataContext 方法](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

