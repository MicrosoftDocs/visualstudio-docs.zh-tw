---
title: 加入至設計工具的物件使用了不同的資料連線
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 915860c2559335f37869f5c6009f7a38dde6abcd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72640836"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>您要加入至設計工具的物件使用與設計工具不同的資料連線

您要加入此設計工具的物件使用了不同於目前所使用設計工具的資料連接。 是否要取代此設計工具所使用的連接?

當您將專案加入至**物件關聯式設計工具**（**O/R 設計**工具）時，所有專案都會使用一個共用資料連線。 （設計介面代表 <xref:System.Data.Linq.DataContext>，其針對介面上的所有物件使用單一連接）。如果您將物件加入至設計工具，而該物件使用的資料連線與設計工具目前正在使用的資料連線不同，則會顯示此訊息。 若要解決這個錯誤，您可以選擇維持現有的連接。 如果選擇這個選項，就不會加入選取的物件。 您也可以選擇加入物件，並將 <xref:System.Data.Linq.DataContext> 連線重設為新連線。

## <a name="connection-options"></a>連線選項

- 若要將現有的連接取代為所選取物件所使用的連接，請按一下 [**是]** 。

   選取的物件會加入至**O/R 設計**工具，而*DataCoNtext. 連接*會設定為新的連接。

   > [!NOTE]
   > 如果您按一下 **[是]** ，則**O/R 設計**工具上的所有實體類別都會對應至新的連接。

- 若要繼續使用現有的連接，並取消加入選取的物件，請按一下 [**否**]。

   會取消動作。 *DataContext.Connection* 仍然會設定為現有的連線。

## <a name="see-also"></a>請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
