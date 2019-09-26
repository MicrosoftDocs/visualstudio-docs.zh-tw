---
title: 此關聯方法是下列預設插入、更新或刪除方法的支援方法
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 11c5c7d3c8078aa420074e9e32bb132489b169c8
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252950"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>此關聯方法是下列預設插入、更新或刪除方法的支援方法

此關聯方法是下列預設`Insert`、 `Update`或`Delete`方法的支援方法。 如果刪除它，這些方法也會被刪除。 是否要繼續?

選取`DataContext`的方法目前會當做**O/R 設計**工具`Update`上其中`Delete`一個實體類別的`Insert`、或方法的其中一個。 刪除選取的方法會導致使用此方法的實體類別還原為預設的執行時間行為，以便在更新期間執行插入、更新或刪除作業。

## <a name="selected-method-options"></a>選取的方法選項

- 若要刪除選取的方法，使實體類別使用執行時間更新，請按一下 **[是]** 。

   系統會刪除選取的方法，而且任何使用此方法覆寫更新行為的類別都會還原成使用預設 LINQ to SQL 執行時間行為。

- 若要關閉訊息方塊，讓選取的方法保持不變，請按一下 [**否**]。

   會關閉訊息方塊，不進行任何變更。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)