---
title: 在自動屬性及完整屬性之間轉換
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8950ce27e95a59f5425419dcac5bd807193d51b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395409"
---
# <a name="convert-between-auto-property-and-full-property"></a>在自動屬性及完整屬性之間轉換

此重構適用於：

- C#

事項 **：** 將自動執行的屬性轉換成完整屬性。

時機 **：** 屬性的邏輯已變更。

**原因：** 您可以手動將自動執行的屬性轉換為完整屬性，不過，這項功能會自動為您執行工作。 

## <a name="how-to"></a>操作方式

1. 將游標放在屬性名稱上。
2. 按下**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。
3. 從下列兩個選項中選取： 

    選取 [ **轉換為完整屬性**]。

   ![將自動屬性轉換為完整屬性](media/convert-auto-property-to-full-property.png) 

    選取 [ **使用 auto 屬性**]。 

    ![將 full 屬性轉換為 auto 屬性](media/convert-full-property-to-auto-property.png) 

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
