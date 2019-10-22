---
title: 您要加入至設計工具的物件使用的資料連線與設計工具目前使用的不同 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9ec76446aff930475ea5e3ca0133e11b3798b0c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672295"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>您要加入至設計工具的物件使用與設計工具所用的不同資料連接
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您要加入此設計工具的物件使用了不同於目前所使用設計工具的資料連接。 是否要取代此設計工具所使用的連接?

 當您將專案加入至 [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] （[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]）時，所有專案都會使用一個共用資料連線。 （設計介面代表 <xref:System.Data.Linq.DataContext>，其針對介面上的所有物件使用單一連接）。如果您將物件加入至設計工具，而該物件使用的資料連線與設計工具目前正在使用的資料連線不同，則會顯示此訊息。 若要解決這個錯誤，您可以選擇維持現有的連接。 如果選擇這個選項，就不會加入選取的物件。 您也可以選擇加入物件，並將 <xref:System.Data.Linq.DataContext> 連線重設為新連線。

> [!NOTE]
> 如果您按一下 [**是]** ，[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 上的所有實體類別都會對應至新的連接。

### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>若要將現有的連接取代為所選取物件使用的連接

- 按一下 [ **是**]。

     選取的物件會加入至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，而且 DataContext.Connection 會設定為新的連接。

### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>若要繼續使用現有的連接並取消加入選取的物件

- 按一下 [否]。

     會取消動作。 DataContext.Connection 仍然會設定為現有的連接。

## <a name="see-also"></a>請參閱
 [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)