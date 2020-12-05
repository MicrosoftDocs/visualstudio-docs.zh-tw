---
title: 從函式產生私用欄位和屬性
description: 瞭解如何使用 [快速動作與重構] 功能表，從函式產生私用欄位或屬性。
ms.custom: SEO-VS-2020
ms.date: 06/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: e989efed8b58746312ed5f5a510efa049393f3db
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617457"
---
# <a name="generate-private-field-and-property-from-constructor"></a>從函式產生私用欄位和屬性

此重構適用於： 

- C# 

事項 **：** 從函式產生私用欄位或屬性。 

時機 **：** 您想要從函式快速新增和初始化私用欄位或屬性。

**原因：** 撰寫私用欄位和屬性可能既耗時又重複。 使用此重構功能既快速，又可讓程式更加健全。

## <a name="how-to"></a>操作方式 

1. 將游標放在函式中的參數名稱上。

2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。
   
3. 接著，選取下列其中一項：

- **建立和初始化欄位，** 或 **建立和初始化屬性**。

   ![從建構函式產生私人欄位](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>另請參閱 

- [重構](../refactoring-in-visual-studio.md)
