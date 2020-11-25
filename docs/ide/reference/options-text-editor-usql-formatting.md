---
title: U-SQL 編輯器格式化選項
description: 瞭解如何在使用 SQL-DMO 進行程式設計時，使用 [格式化選項] 頁面及其子頁面，設定在程式碼編輯器中格式化程式碼的選項。
ms.custom: SEO-VS-2020
ms.date: 01/17/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.General
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bf65c6c80bbcf24d48f5da584349cc4d6b26049
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040286"
---
# <a name="options-text-editor-u-sql-formatting"></a>選項、文字編輯器、U-SQL、格式化

您可以使用 [ **格式化** 選項] 頁面，設定在程式碼編輯器中格式化程式碼的選項。 若要存取此選項頁面，請選擇 [**工具**  >  **選項**]。 在 [選項] 對話方塊中，選擇 [文字編輯器] > [U-SQL] > [格式化]。

## <a name="general-page"></a>[一般] 頁面

### <a name="general-settings"></a>一般設定

這些設定「會在」程式碼編輯器將格式化選項套用至程式碼時有影響。

- **在輸入分號時自動將完成的陳述式格式化**

   選取時，系統會在您根據為編輯器選取的格式化選項選擇分號索引鍵時來格式化陳述式。

- **貼上時自動格式化**

   選取時，系統會將貼入編輯器的文字格式化，使其符合為編輯器選取的格式化選項。

## <a name="preview-windows"></a>預覽視窗

[縮排]、[新行] 和 [間距] 子頁面都會在底部顯示預覽視窗。 預覽視窗會呈現每個選項的效果。 若要使用預覽視窗，請選取一個格式化選項。 預覽視窗會呈現所選選項的範例。 當您選取核取方塊以變更設定時，預覽視窗會更新以顯示新設定的影響。

### <a name="indentation-remarks"></a>縮排備註

每種語言的索引卷 **標頁上** 的縮排選項只會決定當您在行尾按下 **enter** 時，程式碼編輯器放置游標的位置。 [格式化] 下的縮排選項適用於自動格式化程式碼的情況，例如：

- 當您將程式碼貼到檔案中，同時已選取 [貼上時自動格式化] 時
- 當正在格式化的區塊是手動輸入時

## <a name="see-also"></a>另請參閱

- [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)
