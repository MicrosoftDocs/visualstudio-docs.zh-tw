---
title: 針對未匯入的型別完成 IntelliSense
description: 如何針對您尚未匯入的型別搭配 `using` 指示詞使用 IntelliSense 完成。
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
ms.openlocfilehash: 04ea7c94d3dd24c1a511544adca9bfac3370cd71
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094264"
---
# <a name="intellisense-completion-for-unimported-types"></a>針對未匯入的型別完成 IntelliSense

此重構適用於：

- C#

- Visual Basic

**內容：** IntelliSense 為未導入的類型提供完成。

**何時：** 您希望添加一個已在專案中具有依賴項但導入語句尚未添加到檔中的類型。 

**原因：** 您不必手動將導入語句添加到檔中。

## <a name="how-to"></a>操作方式

1. 在您開始使用專案中已經有相依性的型別時，IntelliSense 將會提供建議。
2. 按**選項卡**。 

   匯入陳述式將會新增至您的檔案。

   ![針對未匯入的型別完成 IntelliSense](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)
