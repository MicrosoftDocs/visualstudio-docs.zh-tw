---
title: 將成員設為靜態
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1ecc66cb58ad11bd431acb341dae0493ce8192da
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515299"
---
# <a name="make-member-static"></a>將成員設為靜態

此重構適用於：

- C#

**功能：** 將成員設為靜態。

時機 **：** 您希望非靜態成員為靜態。

**原因：** 靜態成員可改善可讀性：瞭解特定程式碼是隔離的，讓您更容易瞭解、重新讀取和重複使用。 

## <a name="how-to"></a>操作方式

1. 將您的插入號放在成員名稱上。

2. 在字行任何地方按 **Ctrl**+ **.** ， （期間），以觸發 [**快速動作與重構**] 功能表。

   ![將成員設為靜態](media/make-member-static.png)

3. 選取 [設為靜態]。

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
