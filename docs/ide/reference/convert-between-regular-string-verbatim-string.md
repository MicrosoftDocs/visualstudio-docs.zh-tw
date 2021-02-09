---
title: 在一般和逐字字串常值之間轉換
description: 瞭解如何使用 [快速動作] 和 [重構] 功能表，在一般字串和逐字字串常值之間進行轉換。
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1c335c90183e4c5c97b1a2737a2edd8a1b86fb77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918340"
---
# <a name="convert-between-regular-string-and-verbatim-string-literals-refactoring"></a>在一般字串和逐字字串常值重構之間轉換

此重構適用於：

- C#

事項 **：** 可讓您在一般字串和逐字字串常值之間進行轉換。

時機 **：** 您可以在程式碼中儲存空間或更清楚地提供更清楚的空間。

**原因：** 將逐字字串常值轉換為一般字串常值有助於節省空間。 將一般字串常值轉換為逐字字串常值，可以提供更清楚的說明。

## <a name="how-to"></a>使用方法

1. 將插入號放在一般字串或逐字字串常值：

2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

3. 選取下列其中一個選項：

    選取 [Convert to regular string] \(轉換為一般字串\)。

    ![轉換成一般字串](media/convert-to-regular-string.png)

    選取 [Convert to verbatim string] \(轉換為逐字字串\)。

    ![轉換為逐字字串](media/convert-to-verbatim-string.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)