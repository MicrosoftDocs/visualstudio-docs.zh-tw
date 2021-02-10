---
title: 新增 DebuggerDisplay 屬性
description: 瞭解如何新增 DebuggerDisplay 屬性，以控制偵錯工具變數視窗如何顯示物件、屬性或欄位。
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2166f7876909f62d9d16a2a6d5ec126d4544193e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956720"
---
# <a name="add-debuggerdisplay-attribute"></a>新增 DebuggerDisplay 屬性

此程式碼產生適用於：

- C#

事項 **：**[DebuggerDisplay 屬性](../../debugger/using-the-debuggerdisplay-attribute.md)可控制物件、屬性或欄位在偵錯工具變數視窗中顯示的方式。

時機 **：** 您想要以程式設計方式在程式碼中 [釘選屬性](../../debugger/view-data-values-in-data-tips-in-the-code-editor.md#pin-properties-in-datatips)。

**原因：** 釘選屬性可讓您依物件的屬性快速檢查物件，方法是將該屬性反升到偵錯工具內物件的屬性清單頂端。 

## <a name="how-to"></a>使用方法

1. 將游標放在類型、委派、屬性或欄位上。 

2. 按下 **Ctrl** + **。** 以觸發 [ **快速動作與重構** ] 功能表，然後選取 [ **加入 DebuggerDisplay 屬性**]。

    ![產生比較運算子](media/add-debugger-display-attribute.png)

3. DebuggerDisplay 屬性將會連同會傳回預設 ToString ( # A1 的 auto 方法一起加入。 

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)