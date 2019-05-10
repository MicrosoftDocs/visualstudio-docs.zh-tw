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
ms.openlocfilehash: a5ae70462079589ba2b63ee50cf0b7a0570e056a
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457832"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>此關聯方法是下列預設插入、更新或刪除方法的支援方法

此關聯方法是下列預設的支援方法`Insert`， `Update`，或`Delete`方法。 如果刪除它，這些方法也會被刪除。 是否要繼續?

所選`DataContext`方法目前正做為其中一個`Insert`， `Update`，或`Delete`上的實體類別的其中一個方法**O/R Designer**。 刪除選取的方法會使要還原為預設執行階段行為，執行插入，使用這個方法的實體類別更新，或在更新期間刪除。

## <a name="selected-method-options"></a>選取的方法選項

- 若要刪除選取的方法，讓實體類別使用執行階段更新，按一下**是**。

   會刪除選取的方法，而且任何使用這個方法覆寫更新行為的類別都會還原成使用預設 LINQ to SQL 執行階段行為。

- 若要關閉訊息方塊中，保留選取的方法不會變更，按一下**No**。

   會關閉訊息方塊，不進行任何變更。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)