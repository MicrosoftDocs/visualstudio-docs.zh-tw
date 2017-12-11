---
title: "程式碼片段選擇器 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.expansionpicker
helpviewer_keywords:
- Code Snippet Picker
- IntelliSense code snippets, Code Snippet Picker
- code snippets, Code Snippet Picker
ms.assetid: f0862d48-fbbc-4cfe-b228-24492d5c89c4
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 58f419d52d2d89f998f64e236cfc1f0053c9cfd1
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2017
---
# <a name="code-snippet-picker"></a>程式碼片段選擇器
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 程式碼編輯器提供了 [程式碼片段選擇器] ，讓您只需按幾下滑鼠即可將現成的程式碼區塊插入至使用中文件。  
  
 顯示 [程式碼片段選擇器] 的程序會根據所使用的語言而有所不同。  
  
-   [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] - 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著選取 [插入程式碼片段]。  
  
-   [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] - 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著按一下 [插入程式碼片段] 或 [範圍陳述式]。  
  
-   [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] - 無法使用 [程式碼片段選擇器]。  
  
-   Visual F# - 無法使用 [程式碼片段選擇器]。  
  
-   [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] -- 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著按一下 [插入程式碼片段] 或 [範圍陳述式]。  
  
-   XML - 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著按一下 [插入程式碼片段] 或 [範圍陳述式]。  
  
-   HTML - 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著按一下 [插入程式碼片段] 或 [範圍陳述式].。  
  
-   SQL - 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著按一下 [插入程式碼片段]。  
  
在大部分的 Visual Studio 開發語言中，您可以使用 [程式碼片段管理員] 將資料夾新增至 [資料夾清單]，[程式碼片段選擇器] 會掃描那些資料夾中是否有 XML程式碼片段檔案。 您也可以建立自己的程式碼片段並新增至清單。 如需詳細資訊，請參閱[逐步解說：建立程式碼片段](../../ide/walkthrough-creating-a-code-snippet.md)。  
  
## <a name="uielement-list"></a>UIElement 清單  
項目名稱  
可編輯的文字欄位，它會顯示 [項目清單] 中已選取項目的名稱。 若要累加搜尋您想要的項目，請在這個欄位開始鍵入項目名稱。 繼續新增字母，直到 [項目清單] 中選取了所需項目為止。  
  
項目清單  
可供插入的程式碼片段清單，或是含有程式碼片段的資料夾清單。 若要插入程式碼片段或展開資料夾，請選取您要的項目並按 Enter。  
  
## <a name="see-also"></a>另請參閱  
[使用程式碼片段的最佳做法](../../ide/best-practices-for-using-code-snippets.md)   
[Visual Basic IntelliSense 程式碼片段](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)   
[在程式碼中設定書籤](../../ide/setting-bookmarks-in-code.md)   
[如何：使用範圍陳述式程式碼片段](../../ide/how-to-use-surround-with-code-snippets.md)