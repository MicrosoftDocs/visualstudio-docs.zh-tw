---
title: IntelliSense、C#、文字編輯器、選項
description: '瞭解如何使用 c # 區段中的 [IntelliSense] 頁面，修改影響 c # 之 IntelliSense 行為的設定。'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
helpviewer_keywords:
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 9181961c1f30a96e5b03434f4ab686024992e29a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944013"
---
# <a name="options-text-editor-c-intellisense"></a>IntelliSense、C#、文字編輯器、選項

使用 [IntelliSense] 選項頁修改影響 C# 之 IntelliSense 行為的設定。 若要存取此選項頁面，請選擇 [**工具**  >  **選項**]，然後選擇 [**文字編輯器**]  >  **c #**  >  **IntelliSense**。

[IntelliSense] 頁面包含下列選項：

## <a name="completion-lists"></a>完成清單

- 輸入一個字元後顯示完成清單*

   選取這個選項時，IntelliSense 會在您開始輸入時自動顯示完成清單。 未選取這個選項時，仍然可以從 [IntelliSense] 功能表或按 **CTRL**+**空格鍵** 來使用 IntelliSense 完成。

- 在刪除字元後顯示完成清單

- 醒目提示完成清單項目的相符部分

- 顯示完成項目篩選

## <a name="snippets-behavior"></a>程式碼片段行為

- 一律不包含程式碼片段

   選取這個選項時，IntelliSense 一律不會將 C# 程式碼片段的別名新增至完成清單。

- 一律包含程式碼片段

   選取這個選項時，IntelliSense 會將 C# 程式碼片段的別名新增至完成清單。 如果程式碼片段別名與關鍵字相同 (例如 [class](/dotnet/csharp/language-reference/keywords/class))，則會將關鍵字取代為快速鍵。 如需詳細資訊，請參閱 [C# 程式碼片段](../../ide/visual-csharp-code-snippets.md)。

- 在識別碼後鍵入 ?-Tab 時包含程式碼片段

   選取此選項時，IntelliSense 會將 c # 程式碼片段的別名新增至完成清單（若有的話） **？** +識別碼之後按下 **Tab 鍵**

## <a name="enter-key-behavior"></a>ENTER 鍵行為

- 一律不在按下 ENTER 鍵時加入新行

   指定在完成清單中選取項目之後，一律不會自動新增新的一行，然後按 **Enter**。

- 僅在完整輸入的字結尾處按 ENTER 鍵時加入新行

   指定如果您對完成清單中的項目輸入所有字元，然後按 **ENTER** ，則會自動新增新的一行，並將游標移到這個新行。

   例如，如果您輸入 `else`，然後按 **ENTER**，則編輯器中會顯示下列項目：

   `else`

   `|` (游標位置)

   不過，如果您只輸入 `el`，然後按 **ENTER**，則編輯器中會顯示下列項目︰

   `else|` (游標位置)

- 一律在按下 ENTER 鍵時加入新行

   指定如果您對完成清單中的項目輸入「任何字元」，然後按 **ENTER**，則會自動新增新的一行，並將游標移到這個新行。

## <a name="show-name-suggestions"></a>顯示名稱建議

針對您最近選取的成員執行自動物件名稱完成。

## <a name="see-also"></a>另請參閱

- [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)
- [使用 IntelliSense](../../ide/using-intellisense.md)
