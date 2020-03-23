---
title: 顯示導入專案
description: 使用"顯示導入專案"在 Mac 視覺化工作室中展開"IntelliSense"。
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451507"
---
# <a name="show-import-items"></a>顯示導入專案

Mac 的 Visual Studio 可以在 IntelliSense 完成清單中顯示所有可用的類型，即使它們未導入到您的專案。 通過選擇未導入的項，正確的`using`語句將添加到原始檔案中。

![顯示導入專案概述](media/importitems-overview.gif)

## <a name="how-to-enable"></a>如何啟用

要啟用此功能，請通過**視覺化工作室** > **首選項**打開**首選項**，然後導航到**文字編輯器** > **IntelliSense**。 選中"**顯示導入專案**"以啟用 IntelliSense 中的其他專案。

![顯示導入專案選項](media/show-import-items.png)

## <a name="usage"></a>使用量

啟用 **"顯示導入項"** 後，使用該功能導入專案的過程類似于 IntelliSense 中的正常操作。 鍵入代碼時，有效的項將填充完成清單。 這包括尚未導入的專案。 未導入的項將在專案右側顯示其完整命名空間，從而允許您查看要導入的專案。

![顯示導入項清單](media/show-import-items-list.png)

在 IntelliSense 清單中，命名空間顯示在當前未由`using`語句引用的成員旁邊。 如果從清單中選擇這些專案之一，成員將添加到您的代碼_中，_`using`該語句將添加到檔的頂部。 編碼中已引用的類型的成員不會在 IntelliSense 中顯示其命名空間。

## <a name="see-also"></a>另請參閱

- [快速動作 (Windows 上的 Visual Studio)](/visualstudio/ide/quick-actions)
- [重構程式碼 (Windows 上的 Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)
