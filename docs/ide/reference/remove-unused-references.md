---
title: 移除未使用的參考
description: 瞭解如何清除未使用新的 [移除未使用的參考] 命令的專案參考和 NuGet 套件。
ms.custom: SEO-VS-2021
ms.date: 06/01/2021
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 707769229ad7bc1864a135bade1df918d4b27847
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2021
ms.locfileid: "111352082"
---
# <a name="remove-unused-references"></a>移除未使用的參考

此重構適用於：

- C#
- Visual Basic

事項 **：** 可讓您移除未使用的參考。

時機 **：** 您想要清除沒有使用方式的專案參考和 NuGet 套件。 

**原因：** 移除沒有使用方式的專案參考有助於節省空間並縮短應用程式的啟動時間，因為這需要一些時間來載入每個模組，並避免編譯器載入永遠不會使用的中繼資料。

## <a name="how-to"></a>操作方式

1. 在方案總管中，以滑鼠右鍵按一下 [專案名稱] 或 [相依性] 節點。

2. 選取 [ **移除未使用的參考**]。

    ![移除未使用的參考命令](media/remove-unused-references-command.png)

3. [ **移除未使用的參考** ] 對話方塊將會開啟，顯示原始程式碼中沒有使用方式的參考。 您可以選取 [動作] 下拉式清單中的選項，預先選取要移除的未使用參考，以及保留參考的選項 `Keep` 。

    ![移除未使用的參考對話方塊](media/remove-unused-references-dialog.png)

5. 按一下 `Apply` 以移除選取的參考。 

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)