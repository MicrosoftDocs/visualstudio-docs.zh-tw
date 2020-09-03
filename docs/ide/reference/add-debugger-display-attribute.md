---
title: 新增 DebuggerDisplay 屬性
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 611df048d4ce569c10ae933be9053acf1174c06f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85290164"
---
# <a name="add-debuggerdisplay-attribute"></a>新增 DebuggerDisplay 屬性

此程式碼產生適用於：

- C#

事項 **：**[DebuggerDisplay 屬性](https://docs.microsoft.com/visualstudio/debugger/using-the-debuggerdisplay-attribute)可控制物件、屬性或欄位在偵錯工具變數視窗中顯示的方式。

時機 **：** 您想要以程式設計方式在程式碼中[釘選屬性](https://docs.microsoft.com/visualstudio/debugger/view-data-values-in-data-tips-in-the-code-editor#pin-properties-in-datatips)。

**原因：** 釘選屬性可讓您依物件的屬性快速檢查物件，方法是將該屬性反升到偵錯工具內物件的屬性清單頂端。 

## <a name="how-to"></a>操作方式

1. 將游標放在類型、委派、屬性或欄位上。 

2. 按下**Ctrl** + **。** 以觸發 [ **快速動作與重構** ] 功能表，然後選取 [ **加入 DebuggerDisplay 屬性**]。

    ![產生比較運算子](media/add-debugger-display-attribute.png)

3. DebuggerDisplay 屬性將會連同會傳回預設 ToString ( # A1 的 auto 方法一起加入。 

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
