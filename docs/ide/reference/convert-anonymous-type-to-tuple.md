---
title: 將匿名型別轉換為元組
description: 瞭解如何使用 [快速動作與重構] 功能表，將匿名型別轉換為 Visual Studio 中的元組。
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6486b771207722c64993d5a880894fe07beb99c9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907664"
---
# <a name="convert-anonymous-type-to-tuple"></a>將匿名型別轉換為元組

此重構適用於：

- C#

- Visual Basic

事項 **：** 將匿名型別轉換為元組。

時機 **：** 您有一個限定為元組的匿名型別。

**原因：** [元組](/dotnet/csharp/tuples) 有助於將您的語法保持輕量。 這個快速動作讓這項 C# 功能運用上更加輕鬆。

## <a name="how-to"></a>使用方法

1. 將游標放在匿名型別中。
2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

   ![將匿名型別轉換為元組](media/convert-anon-to-tuple.png)

2. 按 **Enter** 鍵接受重構。

   ![將匿名型別轉換為已接受的元組](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
