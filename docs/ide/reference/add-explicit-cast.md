---
title: 新增明確的轉換
ms.date: 03/26/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e159082266b848ce4742e436c706f3f71b2cc9ea
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182972"
---
# <a name="add-explicit-cast"></a>新增明確的轉換

此程式碼產生適用於：

- C#

**功能：** 可讓您根據使用方式，自動將明確轉換加入至運算式。

時機 **：** 您需要將明確轉換新增至運算式，並想要正確地自動指派。

**原因：** 您可以手動將明確轉換加入運算式，不過，這項功能會根據程式碼內容自動新增。

## <a name="how-to-use-it"></a>如何使用

1. 將插入號放在錯誤上。
2. 按**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。
3. 選取 [**新增明確轉換**]。

   ![在 Visual Studio 中新增明確的轉換快速動作](media/add-explicit-cast.png)

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [重構](../refactoring-in-visual-studio.md)
