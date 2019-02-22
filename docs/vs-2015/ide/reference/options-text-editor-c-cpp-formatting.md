---
title: 格式、C/C++、文字編輯器、選項 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 767bb04bcfe14c8cafbe69e5cb19ecbd8082ee40
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54770635"
---
# <a name="options-text-editor-cc-formatting"></a>格式、C/C++、文字編輯器、選項
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
讓您在使用 C 或 C++ 進行程式設計時，變更 [程式碼編輯器] 的預設行為。  
  
 若要存取這個頁面，請在 [選項] 對話方塊的左窗格中依序展開 [文字編輯器] 和 [C/C++]，然後按一下 [格式]。  
  
> [!NOTE]
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
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
 選取這個選項時，會啟用 [pragma 指示詞](http://msdn.microsoft.com/library/9867b438-ac64-4e10-973f-c3955209873f)的自動大綱。 這可讓您在大綱模式下展開或摺疊 Pragma 區域區塊。  
  
 **陳述式區塊的自動大綱**  
 選取這個選項時，會啟用下列陳述式結構的自動大綱：  
  
-   [if-else](http://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2)  
  
-   [switch 陳述式 (C++)](http://msdn.microsoft.com/library/6c3f3ed3-5593-463c-8f4b-b33742b455c6)  
  
-   [while 陳述式 (C++)](http://msdn.microsoft.com/library/358dbe76-5e5e-4af5-b575-c2293c636899)  
  
## <a name="see-also"></a>請參閱  
 [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)   
 [使用 IntelliSense](../../ide/using-intellisense.md)
