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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4e5ca0c60511ee9537041f3a41f44a0e1f55b5a2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441358"
---
# <a name="options-text-editor-c-intellisense"></a>IntelliSense、C#、文字編輯器、選項
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用 [IntelliSense] 屬性頁修改影響 Visual C# 之 IntelliSense 行為的設定。 您可以存取 [IntelliSense] 屬性頁，方法是按一下 [工具] 功能表上的 [選項]，並按一下 [文字編輯器] 資料夾中的 [C#]，然後按一下 [IntelliSense]。  
  
> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
 [IntelliSense] 屬性頁包含下列屬性：  
  
## <a name="completion-lists"></a>完成清單  
 **輸入一個字元後顯示完成清單**  
 選取這個選項時，IntelliSense 會在您開始輸入時自動顯示完成清單。 未選取這個選項時，仍然可以從 [IntelliSense] 功能表或按「CTRL+空格鍵」來使用 IntelliSense 完成。  
  
 **將關鍵字置於完成清單中**  
 選取這個選項時，IntelliSense 會將 C# 關鍵字 (例如 [class](http://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690)) 新增至完成清單。  
  
 **將程式碼片段置於完成清單中**  
 選取這個選項時，IntelliSense 會將 C# 程式碼片段的別名新增至完成清單。 如果程式碼片段別名與關鍵字相同 (例如 [class](http://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690))，則會將關鍵字取代為快速鍵。 如需詳細資訊，請參閱 [Visual C# 程式碼片段](../../ide/visual-csharp-code-snippets.md)。  
  
## <a name="selection-in-completion-lists"></a>完成清單中的選取範圍  
 **輸入下列字元予以認可:**  
 指定在輸入字元之後，這些字元即會對完成清單中的所選取項目執行 IntelliSense 自動完成。  
  
 **按空格鍵予以認可**  
 指定以包含按空格鍵以對完成清單中所選取項目執行 IntelliSense 自動完成的動作。  
  
 **在完整輸入的字結尾處按 ENTER 時新增行**  
 指定如果您對完成清單中的項目輸入所有字元，然後按 ENTER ，則會自動建立新的一行，並將游標移到這個新行。  
  
 例如，如果您輸入 `else`，然後按 ENTER，則編輯器中會顯示下列項目︰  
  
 `else`  
  
 `|` (游標位置)  
  
 不過，如果您只輸入 `el`，然後按 ENTER，則編輯器中會顯示下列項目︰  
  
 `else|` (游標位置)  
  
## <a name="intellisense-member-selection"></a>IntelliSense 成員選取  
 **預先選取最近使用的成員**  
 選取這個選項時，IntelliSense 會預先選取您最近在 [列出成員] 快顯方塊中選取的成員，以在整合式開發環境 (IDE) 中於目前工作階段期間自動補齊物件名稱。 IDE 會在每個工作階段之間，清除最近使用過的成員記錄。 如需詳細資訊，請參閱[用於最近一次使用之成員的 IntelliSense](../../misc/intellisense-for-most-recently-used-members.md)。  
  
## <a name="see-also"></a>請參閱  
 [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)   
 [XML 文件註解](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)   
 [使用 IntelliSense](../../ide/using-intellisense.md)
