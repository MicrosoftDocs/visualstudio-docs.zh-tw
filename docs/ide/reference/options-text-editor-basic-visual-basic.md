---
title: 選項、文字編輯器、基本 (VB)、進階
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.Advanced
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ca2178b61aa3cd2aa83314f00c231d564a10944
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871235"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>選項、文字編輯器、基本 (Visual Basic)、進階
位於 [選項] ([工具] 功能表) 對話方塊上 [文字編輯器] 資料夾的[基本] 資料夾中的 [VB 專用] 屬性頁面包含下列屬性：

 **啟用參考和關鍵字的反白顯示**

文字編輯器可以反白顯示符號的所有執行個體或子句中的所有關鍵字，例如 `If..Then`、`While...End While` 或 `Try...Catch...Finally`。 您可以按 **Ctrl** + **Shift** + **向下鍵**或 **Ctrl** + **Shift** + **向上鍵**，在反白顯示的參考或關鍵字之間巡覽。

**啟用大綱模式**

當您在程式碼編輯器中開啟檔案時，可以使用大綱模式檢視文件。 如需詳細資訊，請參閱[大綱](../../ide/outlining.md)。 選取此選項後，在您開啟檔案時將會啟動大綱功能。

**顯示程序行分隔符號**

文字編輯器會指出程序的可見範圍。 會在專案的 *.vb* 原始程式檔中描繪一行，而這些原始程式檔是位於下表所列的位置：

|vb 原始程式檔中的位置|行位置的範例|
|---------------------------------|------------------------------|
|在區塊宣告建構關閉之後|-   在類別、結構、模組、介面和列舉的結尾處<br />-   在屬性、函式或子函式之後<br />-   不在屬性中的 get 與 set 子句之間|
|在一組的單一行建構之後|-   在重要的陳述式之後，類別檔中的型別定義之前<br />-   在類別中宣告的變數之後，任何程序之前|
|在單一行宣告 (非區塊層級宣告) 之後|-   接在重要的陳述式、繼承陳述式、變數宣告、事件宣告、委派宣告和 DLL 宣告陳述式之後|

 **程式碼美化排列 (重新格式化)** 文字編輯器會適當地重新格式化您的程式碼。 選取此選項後，程式碼編輯器將會：

-   將您的程式碼對齊正確的定位點位置

-   重新將關鍵字、變數和物件指定為正確的大小寫

-   將遺漏的 `Then` 新增至 `If...Then` 陳述式

-   將括弧新增至函式呼叫

-   將遺漏的結尾引號新增至字串

-   重新格式化指數標記法

-   重新格式化日期

**自動插入 End 建構**

 在您輸入 (例如程序宣告 `Sub Main—` 的第一行 ) 並按 **Enter** 時，文字編輯器會新增對稱的 `End Sub` 行。 同樣地，如果新增 [For](/dotnet/visual-basic/language-reference/statements/for-next-statement) 迴圈，則文字編輯器會新增對稱的 `Next` 陳述式。 選取此選項後，程式碼編輯器會自動新增 End 建構。

**自動插入 Interface 及 MustOverride 成員**

當您認可 `Implements` 陳述式或類別的 `Inherits` 陳述式時，文字編輯器就會插入必須各自實作或覆寫之成員的原型。

**啟用錯誤修正建議**

文字編輯器可以提供一般錯誤的解決方案建議，並讓您選取要套用到程式碼的適當修正措施。

## <a name="see-also"></a>請參閱

- [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)
- [索引標籤、所有語言、文字編輯器、選項](../../ide/reference/options-text-editor-all-languages-tabs.md)