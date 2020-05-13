---
title: 從建構函式產生私人欄位
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4eb5dd39d0fb2d4cd9ba8ade0d0408d6e36a4854
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094026"
---
# <a name="generate-private-field-from-constructor"></a>從建構函式產生私人欄位

此重構適用於： 

- C# 

- Visual Basic

**內容：** 從建構函式生成私有欄位。 

**何時：** 您希望從建構函式快速添加私有欄位。

**原因：** 編寫私有欄位可能既耗時又重複。 使用此重構功能既快速，又可讓程式更加健全。

## <a name="how-to"></a>操作方式 

1. 將游標放在建構函式中的參數名稱上。

2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。
   
3. 選擇"**創建和初始化欄位**"選項。

   ![從建構函式產生私人欄位](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>另請參閱 

- [Refactoring](../refactoring-in-visual-studio.md)
