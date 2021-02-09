---
title: 將匿名型別轉換為類別
description: 瞭解如何使用 [快速動作與重構] 功能表，將匿名型別轉換為 Visual Studio 中的類別。
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
monikerRange: '>= vs-2019'
ms.openlocfilehash: 19e755e4b56675265d85a416684f2b42bd7ccd13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907656"
---
# <a name="convert-anonymous-type-to-class"></a>將匿名型別轉換為類別

此重構適用於：

- C#

- Visual Basic

事項 **：** 將匿名型別轉換為類別。

時機 **：** 您有想要在類別中繼續建立的匿名型別。

**原因：** 如果匿名型別只在本機使用，匿名型別就很有用。 隨著您的程式碼增加，輕鬆地將其升階至類別會很有幫助。

## <a name="how-to"></a>使用方法

1. 將游標放在匿名型別中。
2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

   ![將匿名型別轉換為類別](media/convert-anon-to-class.png)

2. 按 **Enter** 鍵接受重構。

   ![已接受將匿名型別轉換為類別](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
