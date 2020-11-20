---
title: 屬性參與關聯
description: 無法刪除屬性，因為它正在參與關聯。 物件關聯式設計工具 (O/R 設計工具) 訊息的詳細資訊，請參閱。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a0d39fa3d7740996be3fc9da75224739f1e55539
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998369"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>無法刪除屬性&lt;屬性名稱&gt;，因為其正在參與關聯&lt;關聯名稱&gt;

選取的屬性，已設定為在錯誤訊息指出之類別 (Class) 之間進行關聯時所需的 **關聯屬性**。 如果屬性已參與資料類別之間的關聯，就無法刪除屬性。

將 **關聯屬性** 設定為資料類別的不同屬性，就可以成功刪除需要刪除的屬性。

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 在 **O/R 設計工具** 上，選取在錯誤訊息指出的資料類別之間連接的關聯線。

2. 按兩下這條線以開啟 [關聯編輯器] 對話方塊。

3. 從 [關聯屬性] 中移除屬性。

4. 試著再次刪除屬性。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)