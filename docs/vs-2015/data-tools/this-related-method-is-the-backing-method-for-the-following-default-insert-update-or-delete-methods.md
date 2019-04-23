---
title: 此關聯方法是下列預設插入、 更新或刪除方法的支援方法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 53b27637a270e18ae56809cce8c478de1929b48e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111788"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>此關聯方法是下列預設插入、更新或刪除方法的支援方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此關聯方法是下列預設插入、更新或刪除方法的支援方法。 如果刪除它，這些方法也會被刪除。 是否要繼續?  
  
 選取的 `DataContext` 方法目前是當成 O/R 設計工具上某個實體類別 (Class) 的插入、更新或刪除方法。 刪除選取的方法會將使用這個方法的實體類別，還原成在更新期間執行插入、更新或刪除作業的預設執行階段行為。  
  
### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>若要刪除選取的方法以讓實體類別使用執行階段更新  
  
- 按一下 [ **是**]。  
  
     會刪除選取的方法，而且任何使用這個方法覆寫更新行為的類別都會還原成使用預設 LINQ to SQL 執行階段行為。  
  
### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>若要關閉訊息方塊並保留選取的方法  
  
- 按一下 [否] 。  
  
     會關閉訊息方塊，不進行任何變更。  
  
## <a name="see-also"></a>另請參閱  
 [DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)   
 [如何：指定預存程序，以執行更新、 插入和刪除 （O/R 設計工具）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
