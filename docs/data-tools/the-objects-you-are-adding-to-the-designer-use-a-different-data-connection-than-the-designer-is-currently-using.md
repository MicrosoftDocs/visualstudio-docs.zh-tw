---
title: 您要加入至設計工具的物件使用與設計工具所用的不同資料連接
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9e0864ec07250ed5886f864d4233aeb902ecf5ae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565618"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>您要加入至設計工具的物件使用不同的資料連接與設計工具

您要加入此設計工具的物件使用了不同於目前所使用設計工具的資料連接。 是否要取代此設計工具所使用的連接?

當您將項目加入**物件關聯式設計工具**(**O/R Designer**)，所有的項目會使用一個共用的資料連接。 (設計介面即代表一個 <xref:System.Data.Linq.DataContext>，這讓介面上的所有物件都會使用單一連接)。如果加入至設計工具的物件所使用的資料連接與設計工具目前使用的資料連接不同，就會顯示這則訊息。 若要解決這個錯誤，您可以選擇維持現有的連接。 如果選擇這個選項，就不會加入選取的物件。 您也可以選擇加入物件，並將 <xref:System.Data.Linq.DataContext> 連線重設為新連線。

## <a name="connection-options"></a>連線選項

- 若要取代現有的連接與所選取的物件使用的連接，請按一下**是**。

   選取的物件加入至**O/R Designer**，而*DataContext.Connection*設為新的連接。

   > [!NOTE]
   > 如果您按一下 **[是]**，所有的實體類別上**O/R Designer**會對應至新的連接。

- 若要繼續使用現有的連線，取消加入選取的物件，按一下**No**。

   會取消動作。 *DataContext.Connection* 仍然會設定為現有的連線。

## <a name="see-also"></a>另請參閱

- [O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)
- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
