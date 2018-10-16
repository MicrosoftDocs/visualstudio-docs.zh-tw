---
title: 您要加入至設計工具的物件使用不同的資料連接，於目前所使用設計工具 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c86b40a79cc91f1a778d6c98be0865dc4a161840
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260919"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>您要加入至設計工具的物件使用與設計工具所用的不同資料連接
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
您要加入此設計工具的物件使用了不同於目前所使用設計工具的資料連接。 是否要取代此設計工具所使用的連接?  
  
 當您將項目加入[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)])，所有的項目會使用一個共用的資料連接。 (設計介面即代表一個 <xref:System.Data.Linq.DataContext>，這讓介面上的所有物件都會使用單一連接)。如果加入至設計工具的物件所使用的資料連接與設計工具目前使用的資料連接不同，就會顯示這則訊息。 若要解決這個錯誤，您可以選擇維持現有的連接。 如果選擇這個選項，就不會加入選取的物件。 或者，您可以選擇將物件加入及重設<xref:System.Data.Linq.DataContext>連接至新的連接。  
  
> [!NOTE]
>  如果您按一下 **[是]**，所有的實體類別上[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]會對應至新的連接。  
  
### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>若要將現有的連接取代為所選取物件使用的連接  
  
-   按一下 [ **是**]。  
  
     選取的物件會加入至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，而且 DataContext.Connection 會設定為新的連接。  
  
### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>若要繼續使用現有的連接並取消加入選取的物件  
  
-   按一下 [否] 。  
  
     會取消動作。 DataContext.Connection 仍然會設定為現有的連接。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)

