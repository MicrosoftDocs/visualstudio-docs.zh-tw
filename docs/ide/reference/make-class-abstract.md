---
title: 將類別設為抽象
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 7b44c8331c10bc0cf2f87e19094a77c0cbec251a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919426"
---
# <a name="make-class-abstract"></a>將類別設為抽象

此重構適用於：

- C#

- Visual Basic

事項 **：** 將類別設為抽象重構。

時機 **：** 您在不是抽象的類別中撰寫抽象方法。

**原因：**  撰寫程式碼以在撰寫抽象方法之後讓類別變成抽象，可節省您的時間。

## <a name="how-to"></a>使用方法

1. 將您的插入號放在抽象方法上。

2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

3. 選取 [ **使類別成為抽象**]。

    ![將類別設為抽象](media/make-class-abstract.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
