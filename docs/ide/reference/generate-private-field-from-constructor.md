---
title: 從自構造函式產生私用欄位
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8ef4188216b669b30b7af9bd725ec432bcd0a774
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527658"
---
# <a name="generate-private-field-from-constructor"></a>從自構造函式產生私用欄位

此重構適用於： 

- C# 

**功能：** 從函式產生私用欄位。 

時機 **：** 您想要從函式快速新增私用欄位。

**原因：** 撰寫私用欄位可能既耗時又重複。 使用此重構功能既快速，又可讓程式更加健全。

## <a name="how-to"></a>操作方式 

1. 將游標放在函式中的參數名稱上。

2. 在字行任何地方按 **Ctrl**+ **.** ， 以觸發 [快速動作與重構] 功能表。
   
3. 選取 [**建立並初始化欄位**] 選項。

   ![從自構造函式產生私用欄位](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>另請參閱 

- [重構](../refactoring-in-visual-studio.md)
