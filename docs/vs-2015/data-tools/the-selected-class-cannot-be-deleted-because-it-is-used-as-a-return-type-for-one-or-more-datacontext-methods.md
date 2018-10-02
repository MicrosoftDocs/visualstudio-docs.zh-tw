---
title: 無法刪除選取的類別，因為它一或多個 DataContext 方法的傳回型別當做使用 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9a285922a004669b75d33ac6d866e1f21f5d6442
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497423"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>無法刪除所選取的類別，因為它是用來當做一或多個 DataContext 方法的傳回型別。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[無法刪除選取的類別，因為它一或多個 DataContext 方法的傳回型別當做使用](https://docs.microsoft.com/visualstudio/data-tools/the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods)。  
  
  
有一個或多個 <xref:System.Data.Linq.DataContext> 方法的傳回型別是選取的實體類別 (Class)。 刪除被 <xref:System.Data.Linq.DataContext> 方法當做傳回型別的實體類別，會使專案編譯作業失敗。 若要刪除選取的實體類別，請識別使用它的 <xref:System.Data.Linq.DataContext> 方法，並將這些方法的傳回型別設定為不同的實體類別。  
  
 若要還原的傳回型別<xref:System.Data.Linq.DataContext>方法，以其原始自動產生的類型，第一次刪除<xref:System.Data.Linq.DataContext>方法，從方法窗格，然後拖曳的物件**伺服器總管**/ **資料庫總管**拖曳至 O/R 設計工具一次。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  找出<xref:System.Data.Linq.DataContext>作為傳回型別中的實體類別，藉由選取的方法<xref:System.Data.Linq.DataContext>方法中的方法窗格，並檢查**傳回型別**中的屬性**屬性**視窗.  
  
2.  設定**傳回型別**不同的實體類別或刪除<xref:System.Data.Linq.DataContext>從方法窗格的方法。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [逐步解說： 建立 LINQ to SQL 類別 （O-R 設計工具）](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)   
 [如何：變更 DataContext 方法的傳回型別 (O/R 設計工具)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)

