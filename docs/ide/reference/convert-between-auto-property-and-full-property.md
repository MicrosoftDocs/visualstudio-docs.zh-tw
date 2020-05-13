---
title: 在自動屬性和完整屬性之間進行轉換
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
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395409"
---
# <a name="convert-between-auto-property-and-full-property"></a>在自動屬性和完整屬性之間進行轉換

此重構適用於：

- C#

**內容：** 在自動實現的屬性之間轉換為完整屬性。

**何時：** 屬性的邏輯已更改。

**原因：** 您可以在自動實現的屬性之間手動轉換為完整屬性，但此功能將自動為您完成工作。 

## <a name="how-to"></a>操作方式

1. 將游標放在屬性名稱上。
2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。
3. 從以下兩個選項中進行選擇： 

    選擇 **"轉換為完整屬性**"。

   ![將自動屬性轉換為完整屬性](media/convert-auto-property-to-full-property.png) 

    選擇 **"使用自動屬性**"。 

    ![將完整屬性轉換為自動屬性](media/convert-full-property-to-auto-property.png) 

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)
