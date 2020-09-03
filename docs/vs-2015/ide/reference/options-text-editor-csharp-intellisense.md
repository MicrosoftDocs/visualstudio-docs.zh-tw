---
title: IntelliSense、C#、文字編輯器、選項 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- IntelliSense [J#], options
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1e3f4df9a7a885245e40f7e9fec1b0da207ada39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662302"
---
# <a name="options-text-editor-c-intellisense"></a>IntelliSense、C#、文字編輯器、選項
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用 [IntelliSense]**** 屬性頁修改影響 Visual C# 之 IntelliSense 行為的設定。 您可以存取 [IntelliSense]**** 屬性頁，方法是按一下 [工具]**** 功能表上的 [選項]****，並按一下 [文字編輯器]**** 資料夾中的 [C#]****，然後按一下 [IntelliSense]****。

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更您的設定，請在 [工具]**** 功能表上選擇 [匯入和匯出設定]****。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。

 [IntelliSense]**** 屬性頁包含下列屬性：

## <a name="completion-lists"></a>完成清單
 在**輸入字元之後顯示完成清單**選取此選項時，IntelliSense 會在您開始鍵入時自動顯示完成清單。 未選取此選項時，intellisense 功能表或按 CTRL + 空格鍵仍然可以 **使用 intellisense 完成** 。

 **將關鍵字放在完成清單中** 選取此選項時，IntelliSense 會將 c # 關鍵字（例如 [類別](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690)）新增至完成清單。

 **將程式碼片段置於完成清單中** 選取此選項時，IntelliSense 會將 c # 程式碼片段的別名新增至完成清單。 如果程式碼片段別名與關鍵字相同 (例如 [class](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690))，則會將關鍵字取代為快速鍵。 如需詳細資訊，請參閱 [Visual C# 程式碼片段](../../ide/visual-csharp-code-snippets.md)。

## <a name="selection-in-completion-lists"></a>完成清單中的選取範圍
 **輸入下列字元來認可：** 指定在輸入完成清單中，針對選取的專案執行 IntelliSense 自動完成的所有字元。

 藉**由按下空格鍵來認可**指定要包含按下空格鍵以針對完成清單中的選取專案執行 IntelliSense 自動完成的動作。

 **在完整類型字尾的輸入上加入新行** 指定如果您在完成清單中輸入專案的所有字元，然後按 ENTER，則會自動建立新的一行，並將游標移至新的一行。

 例如，如果您輸入 `else`，然後按 ENTER，則編輯器中會顯示下列項目︰

 `else`

 `|` (游標位置)

 不過，如果您只輸入 `el`，然後按 ENTER，則編輯器中會顯示下列項目︰

 `else|` (游標位置)

## <a name="intellisense-member-selection"></a>IntelliSense 成員選取
 **預先選取最近使用的成員** 選取此選項時，IntelliSense 會預先選取您最近在 [快顯清單成員] 方塊中選取的成員，以在您的整合式開發環境 (IDE) 期間，自動完成物件名稱自動完成。 IDE 會在每個工作階段之間，清除最近使用過的成員記錄。 如需詳細資訊，請參閱[用於最近一次使用之成員的 IntelliSense](../../misc/intellisense-for-most-recently-used-members.md)。

## <a name="see-also"></a>另請參閱
 [使用 IntelliSense](../../ide/using-intellisense.md)的[一般、環境、選項對話方塊](../../ide/reference/general-environment-options-dialog-box.md) [XML 檔批註](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)
