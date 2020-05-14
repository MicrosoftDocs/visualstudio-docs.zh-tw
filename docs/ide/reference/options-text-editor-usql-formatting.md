---
title: U-SQL 編輯器格式化選項
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
ms.openlocfilehash: 200ec41a1295178f1127d10053985384a7813158
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568265"
---
# <a name="options-text-editor-u-sql-formatting"></a>選項、文字編輯器、U-SQL、格式化

使用 **"格式化**"選項頁設置代碼編輯器中代碼格式的選項。 要訪問此選項頁，請選擇 **"工具** > **選項**"。 在 [選項]**** 對話方塊中，選擇 [文字編輯器]**** > [U-SQL]**** > [格式化]****。

## <a name="general-page"></a>[一般] 頁面

### <a name="general-settings"></a>一般設定

這些設定「會在」** 程式碼編輯器將格式化選項套用至程式碼時有影響。

- **在輸入分號時自動將完成的陳述式格式化**

   選取時，系統會在您根據為編輯器選取的格式化選項選擇分號索引鍵時來格式化陳述式。

- **貼上時自動格式化**

   選取時，系統會將貼入編輯器的文字格式化，使其符合為編輯器選取的格式化選項。

## <a name="preview-windows"></a>預覽視窗

[縮排]****、[新行]**** 和 [間距]**** 子頁面都會在底部顯示預覽視窗。 預覽視窗會呈現每個選項的效果。 若要使用預覽視窗，請選取一個格式化選項。 預覽視窗會呈現所選選項的範例。 當您選取核取方塊以變更設定時，預覽視窗會更新以顯示新設定的影響。

### <a name="indentation-remarks"></a>縮排備註

每種語言的 **"選項卡"** 頁上的縮進選項僅確定代碼編輯器在按行末尾的**Enter**時放置游標的位置。 [格式化]**** 下的縮排選項適用於自動格式化程式碼的情況，例如：

- 當您將程式碼貼到檔案中，同時已選取 [貼上時自動格式化]**** 時
- 當正在格式化的區塊是手動輸入時

## <a name="see-also"></a>另請參閱

- [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)
