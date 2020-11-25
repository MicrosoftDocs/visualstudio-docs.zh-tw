---
title: 在自動屬性及完整屬性之間轉換
description: 瞭解如何使用 [快速動作] 和 [重構] 功能表，在自動執行的屬性和 full 屬性之間轉換。
ms.custom: SEO-VS-2020
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b53f337b538ff1c0aef84272eea7d9e032eb2c1d
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040832"
---
# <a name="convert-between-auto-property-and-full-property"></a>在自動屬性及完整屬性之間轉換

此重構適用於：

- C#

事項 **：** 將自動執行的屬性轉換成完整屬性。

時機 **：** 屬性的邏輯已變更。

**原因：** 您可以手動將自動執行的屬性轉換為完整屬性，不過，這項功能會自動為您執行工作。 

## <a name="how-to"></a>操作方式

1. 將游標放在屬性名稱上。
2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。
3. 從下列兩個選項中選取： 

    選取 [ **轉換為完整屬性**]。

   ![將自動屬性轉換為完整屬性](media/convert-auto-property-to-full-property.png) 

    選取 [ **使用 auto 屬性**]。 

    ![將 full 屬性轉換為 auto 屬性](media/convert-full-property-to-auto-property.png) 

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
