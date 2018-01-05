---
title: "您要加入至設計工具的物件是目前所使用設計工具，請使用不同的資料連線 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 715bb696819af901c04fc0d95747b51186868003
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>您要加入至設計工具的物件使用與設計工具所用的不同資料連接
您要加入此設計工具的物件使用了不同於目前所使用設計工具的資料連接。 是否要取代此設計工具所使用的連接?  
  
 當您將項目加入[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)]([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)])，所有項目都會使用單一的共用的資料連接。 (設計介面即代表一個 <xref:System.Data.Linq.DataContext>，這讓介面上的所有物件都會使用單一連接)。如果加入至設計工具的物件所使用的資料連接與設計工具目前使用的資料連接不同，就會顯示這則訊息。 若要解決這個錯誤，您可以選擇維持現有的連接。 如果選擇這個選項，就不會加入選取的物件。 或者，您可以選擇要將此物件加入並重設<xref:System.Data.Linq.DataContext>連接至新的連接。  
  
> [!NOTE]
>  如果您按一下**是**上的所有實體都類別[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]都會對應至新的連接。  
  
### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>若要將現有的連接取代為所選取物件使用的連接  
  
-   按一下 [ **是**]。  
  
     選取的物件會加入至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，而且 DataContext.Connection 會設定為新的連接。  
  
### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>若要繼續使用現有的連接並取消加入選取的物件  
  
-   按一下 [否] 。  
  
     會取消動作。 DataContext.Connection 仍然會設定為現有的連接。  
  
## <a name="see-also"></a>另請參閱
[O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
 