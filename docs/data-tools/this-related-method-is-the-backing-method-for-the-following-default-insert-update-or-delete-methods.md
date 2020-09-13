---
title: 無法刪除支援方法
description: 此關聯方法是下列預設插入、更新或刪除方法的支援方法
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 66acc8486bcb261bb97a1611ff0c6753caa65dee
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037552"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>此關聯方法是下列預設插入、更新或刪除方法的支援方法

此相關的方法是下列預設 `Insert` 、或方法的支援方法 `Update` `Delete` 。 如果刪除它，這些方法也會被刪除。 是否要繼續?

選取的 `DataContext` 方法目前當做 `Insert` `Update` `Delete` **O/R 設計**工具上其中一個實體類別的其中一個、或方法使用。 刪除選取的方法會導致使用這個方法的實體類別還原成預設執行時間行為，以便在更新期間執行插入、更新或刪除。

## <a name="selected-method-options"></a>選取的方法選項

- 若要刪除選取的方法，使實體類別使用執行時間更新，請按一下 **[是]**。

   系統會刪除選取的方法，並將使用這個方法覆寫更新行為的任何類別還原為使用預設的 LINQ to SQL 執行時間行為。

- 若要關閉訊息方塊，讓選取的方法保持不變，請按一下 [ **否**]。

   會關閉訊息方塊，不進行任何變更。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)