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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "77515299"
---
# <a name="make-member-static"></a>將成員設為靜態

此重構適用於：

- C#

事項 **：** 將成員設為靜態。

時機 **：** 您希望非靜態成員是靜態的。

**原因：** 靜態成員可提高可讀性：知道特定程式碼是隔離的，可讓您更容易瞭解、重新讀取和重複使用。 

## <a name="how-to"></a>操作方式

1. 將您的插入號放在成員名稱上。

2. 按下**Ctrl** + **。** ) 觸發 [ **快速動作與重構** ] 功能表的 (期間。

   ![將成員設為靜態](media/make-member-static.png)

3. 選取 [設為靜態]。

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
