---
title: "選項、文字編輯器、C/C++、格式設定 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- CPP
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5a96a88ca7edd21989764c843f57c01a7bf03b0a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="options-text-editor-cc-formatting"></a>選項、文字編輯器、C/C++、格式設定
讓您在使用 C 或 C++ 進行程式設計時，變更 [程式碼編輯器] 的預設行為。  
  
 若要存取這個頁面，請在 [選項] 對話方塊的左窗格中依序展開 [文字編輯器] 和 [C/C++]，然後按一下 [格式]。  
  
> [!NOTE]
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="cc-options"></a>C/C++ 選項  
 **啟用自動快速諮詢工具提示**  
 啟用或停用 [快速諮詢 IntelliSense] 功能。  
  
## <a name="inactive-code"></a>非現用程式碼  
 **顯示非現用程式碼區塊**  
 因為 `#ifdef` 宣告而變成非現用的程式碼會以不同色彩標示，有助於識別。  
  
 **停用非現用程式碼不透明度**  
 非現用程式碼可以使用色彩而非透明度進行識別。  
  
 **非現用程式碼不透明度百分比**  
 可以自訂非現用程式碼區塊的不透明度程度。  
  
## <a name="indentation"></a>縮排  
 **縮排大括弧**  
 您可以設定在開始程式碼區塊後按下 ENTER 時，括號對齊的方式 (例如，函式或 `for` 迴圈)。 括號可以對齊程式碼區塊的第一個字元或是縮排。  
  
 **使用 Tab 自動縮排**  
 您可以設定按 TAB 鍵時，目前程式碼行會發生什麼狀況。 程式碼行會縮排，或是會插入定位點。  
  
## <a name="miscellaneous"></a>其他  
 **在 [工作清單] 視窗中列舉註解**  
 編輯器可以掃描開啟的原始程式檔，以尋找註解中的預設文字。 它會在 [工作清單] 視窗中為找到的任何關鍵字建立項目。  
  
 **反白顯示相符的語彙基元**  
 當游標位於括號旁邊時，編輯器可以反白顯示對稱的括號，讓您更容易看清楚包含的程式碼。  
  
## <a name="outlining"></a>大綱  
 **檔案開啟時進入大綱模式**  
 在文字編輯器中開啟檔案時，可以啟用大網功能。 如需詳細資訊，請參閱[大綱](../../ide/outlining.md)。 選取這個選項後，在您開啟檔案時將會啟用大綱功能。  
  
 **#pragma 區域區塊的自動大綱**  
 選取這個選項時，會啟用 [pragma 指示詞](/cpp/preprocessor/pragma-directives-and-the-pragma-keyword)的自動大綱。 這可讓您在大綱模式下展開或摺疊 Pragma 區域區塊。  
  
 **陳述式區塊的自動大綱**  
 選取這個選項時，會啟用下列陳述式結構的自動大綱：  
  
-   [if-else](/dotnet/csharp/language-reference/keywords/if-else)  
  
-   [switch 陳述式 (C++)](/cpp/cpp/switch-statement-cpp)  
  
-   [while 陳述式 (C++)](/cpp/cpp/while-statement-cpp)  
  
## <a name="see-also"></a>請參閱  
 [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)   
 [使用 IntelliSense](../../ide/using-intellisense.md)