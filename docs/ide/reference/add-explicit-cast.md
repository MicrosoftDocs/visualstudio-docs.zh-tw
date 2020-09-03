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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "84182972"
---
# <a name="add-explicit-cast"></a>新增明確的轉換

此程式碼產生適用於：

- C#

事項 **：** 可讓您根據使用方式，自動將明確的轉換加入至運算式。

時機 **：** 您必須將明確的轉換加入至運算式，並想要自動正確地指派。

**原因：** 您可以手動將明確轉換加入至運算式，不過，這項功能會根據程式碼內容自動新增。

## <a name="how-to-use-it"></a>用法

1. 將插入號放在錯誤上。
2. 按下**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。
3. 選取 [Add explicit cast] \(新增明確轉換\)。

   ![在 Visual Studio 中新增明確的轉換快速動作](media/add-explicit-cast.png)

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [重構](../refactoring-in-visual-studio.md)
