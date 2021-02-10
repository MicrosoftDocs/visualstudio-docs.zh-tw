---
title: 擷取基底類別
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
ms.openlocfilehash: 8c389ac6285b3f20dcdf05833f1ff3202d155c4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962804"
---
# <a name="extract-base-class"></a>擷取基底類別

此重構適用於：

- C#

- Visual Basic

事項 **：** 解壓縮基類。

時機 **：** 您想要將來自所選類別的成員解壓縮至新的基類。

**原因：** 手動提取成員可能相當耗時，並讓您離開工作流程。 

## <a name="how-to"></a>使用方法

1. 將插入號放在類別名稱或反白顯示的成員上。

2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

3. 選取 [Pull member(s) up to new base class] \(將成員向上提取到新基底類別\)。

    ![[解壓縮基類] 對話方塊](media/extract-base-class.png)

新的 [Extract Base Class] \(擷取基底類別\) 對話方塊隨即開啟，您可以在其中指定基底類別的名稱，以及要放置該類別的位置。 您可以選取要傳送至新基類的成員，並選取 [設為抽象] 資料行中的核取方塊，以選擇讓成員成為抽象類別。

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
