---
title: 將匿名型別轉換為類別
description: 瞭解如何使用 [快速動作與重構] 功能表，將匿名型別轉換為 Visual Studio 中的類別。
ms.custom: SEO-VS-2020
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
monikerRange: '>= vs-2019'
ms.openlocfilehash: a041c077a41ce6b37d74507723ec1ce0f8c9585c
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040781"
---
# <a name="convert-anonymous-type-to-class"></a>將匿名型別轉換為類別

此重構適用於：

- C#

- Visual Basic

事項 **：** 將匿名型別轉換為類別。

時機 **：** 您有想要在類別中繼續建立的匿名型別。

**原因：** 如果匿名型別只在本機使用，匿名型別就很有用。 隨著您的程式碼增加，輕鬆地將其升階至類別會很有幫助。

## <a name="how-to"></a>操作方式

1. 將游標放在匿名型別中。
2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

   ![將匿名型別轉換為類別](media/convert-anon-to-class.png)

2. 按 **Enter** 鍵接受重構。

   ![已接受將匿名型別轉換為類別](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
