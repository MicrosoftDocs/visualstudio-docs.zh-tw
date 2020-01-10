---
title: 顯示匯入專案
description: 使用 [顯示匯入專案] 展開 Visual Studio for Mac 中的 IntelliSense。
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75451507"
---
# <a name="show-import-items"></a>顯示匯入專案

Visual Studio for Mac 可以在 IntelliSense 完成清單中顯示所有可用的類型，即使它們未匯入至您的專案也一樣。 藉由選取未匯入的專案，將會在原始程式檔中新增正確的 `using` 語句。

![顯示匯入專案總覽](media/importitems-overview.gif)

## <a name="how-to-enable"></a>如何啟用

若要啟用這項功能，請**透過 Visual Studio** > **喜好**設定開啟**喜好**設定，並流覽至 [**文字編輯器**] > **IntelliSense**。 核取 [**顯示匯入專案**] 核取方塊，以在 IntelliSense 中啟用其他專案。

![顯示匯入專案選項](media/show-import-items.png)

## <a name="usage"></a>使用

啟用 [**顯示匯入專案**] 之後，使用功能匯入專案的程式會與 IntelliSense 內的一般動作類似。 當您輸入程式碼時，有效的專案將會填入完成清單。 這包括尚未匯入的專案。 未匯入的專案會在專案右邊顯示其完整命名空間，讓您能夠查看要提取至專案的匯入。

![顯示匯入專案清單](media/show-import-items-list.png)

在 IntelliSense 清單中，命名空間會顯示在 `using` 語句目前未參考的成員旁。 如果您從清單中選擇其中一個專案，則會將成員新增至您的程式碼，_並_將 `using` 語句加入至檔案的頂端。 已在程式碼中參考之類型的成員，將不會在 IntelliSense 中顯示其命名空間。

## <a name="see-also"></a>請參閱

- [快速動作 (Windows 上的 Visual Studio)](/visualstudio/ide/quick-actions)
- [重構程式碼 (Windows 上的 Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)
