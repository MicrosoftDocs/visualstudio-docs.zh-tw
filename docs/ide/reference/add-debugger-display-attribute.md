---
title: 加入 DebuggerDisplay 屬性
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 611df048d4ce569c10ae933be9053acf1174c06f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290164"
---
# <a name="add-debuggerdisplay-attribute"></a>加入 DebuggerDisplay 屬性

此程式碼產生適用於：

- C#

**功能：**[DebuggerDisplay 屬性](https://docs.microsoft.com/visualstudio/debugger/using-the-debuggerdisplay-attribute)會控制物件、屬性或欄位在偵錯工具變數視窗中的顯示方式。

時機 **：** 您想要以程式設計方式在程式碼中釘選偵錯工具內的[屬性](https://docs.microsoft.com/visualstudio/debugger/view-data-values-in-data-tips-in-the-code-editor#pin-properties-in-datatips)。

**原因：** 釘選屬性可讓您透過將該屬性反升到偵錯工具內物件屬性清單的頂端，以快速檢查物件的屬性。 

## <a name="how-to"></a>操作方式

1. 將游標放在類型、委派、屬性或欄位上。 

2. 按**Ctrl** + **。** 以觸發 [**快速動作與重構**] 功能表，然後選取 [**新增 DebuggerDisplay 屬性**]。

    ![產生比較運算子](media/add-debugger-display-attribute.png)

3. DebuggerDisplay 屬性會與自動方法一起加入，以傳回預設的 ToString （）。 

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
