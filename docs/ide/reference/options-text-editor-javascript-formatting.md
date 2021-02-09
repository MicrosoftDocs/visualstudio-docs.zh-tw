---
title: Options, Text Editor, JavaScript, Formatting
description: 瞭解如何使用 [選項] 對話方塊的 [格式化] 頁面，設定在程式碼編輯器中格式化程式碼的選項。
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 27b2c5765f041252e62defd15a3c7b6d7b460b43
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932458"
---
# <a name="options-dialog-box-text-editor--javascript--formatting"></a>選項對話方塊：文字編輯器 \> JavaScript \> 格式化

使用 [選項] 對話方塊的 [格式] 頁面，設定在程式碼編輯器中格式化程式碼的選項。 若要存取此頁面，請在功能表列上選擇 [**工具**  >  **選項**]，然後展開 [**文字編輯器**  >  **JavaScript/TypeScript**  >  **格式**]。

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="automatic-formatting"></a>自動格式化

這些選項會決定在 [來源] 檢視中進行格式化的時機。

### <a name="uielement-list"></a>UIElement 清單

|選項|Description|
|------------|-----------------|
|**遇到 Enter 字元時格式化完成的行**|選取這個選項時，程式碼編輯器會在您選擇 Enter 鍵時自動格式化行。|
|**遇到 ; 字元時格式化完成的陳述式**|選取這個選項時，程式碼編輯器會在您選擇分號鍵時自動格式化行。|
|**將 { 上開啟的區塊格式化**|選取這個選項時，程式碼編輯器會在您選擇左大括弧鍵時，對行進行自動格式化。|
|**遇到 } 字元時格式化完成的區塊**|選取這個選項時，程式碼編輯器會在您選擇右大括弧鍵時自動格式化行。|
|**於貼上時格式化**|選取這個選項時，程式碼編輯器會在您將程式碼貼入編輯器時重新格式化程式碼。 編輯器會使用目前定義的格式化規則。 如果未選取這個選項，則編輯器會使用所貼入程式碼的原始格式。|

## <a name="new-lines"></a>新行

這些選項會決定程式碼編輯器是否將函式和控制區塊的左大括弧放在新行。

### <a name="uielement-list"></a>UIElement 清單

|選項|Description|
|------------|-----------------|
|**將函式的左大括弧放在新行**|選取這個選項時，程式碼編輯器會將與函式相關聯的左大括弧移至新行。|
|**將控制區塊的左大括弧置於新行**|選取這個選項時，程式碼編輯器會將與控制區塊 (例如，`if` 和 `while` 控制區塊) 相關聯的左大括弧移至新行。|

## <a name="spacing"></a>間距

這些選項會決定在 [來源] 檢視中插入空格的方式。

### <a name="uielement-list"></a>UIElement 清單

|選項|Description|
|------------|-----------------|
|**在逗號分隔符號後面插入空格**|選取這個選項時，程式碼編輯器會在逗號分隔符號後面新增空格。|
|**在 "for" 陳述式中的分號後面插入空格**|選取這個選項時，程式碼編輯器會在 `for` 迴圈第一行中的每個分號後面新增空格。|
|**在二元運算子前後插入空格**|選取這個選項時，程式碼編輯器會在二元運算子 (例如，+、-、&&、&#124;&#124;) 前後新增空格。|
|**在控制流程陳述式的關鍵字後面插入空格**|選取這個選項時，程式碼編輯器會在控制流程陳述式的 JavaScript 關鍵字後面新增空格。|
|**在匿名函式的函式關鍵字後面插入空格**|選取這個選項時，程式碼編輯器會在匿名函式的 `function` 關鍵字後面新增空格。|
|**在非空白括弧的左括弧後面及右括弧前面插入空格**|選取這個選項時，如果括弧內有非空白字元，則程式碼編輯器會在左括弧後面及右括弧前面新增空格。|

## <a name="see-also"></a>另請參閱

- [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)