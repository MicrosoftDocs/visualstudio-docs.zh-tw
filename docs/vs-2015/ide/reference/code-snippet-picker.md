---
title: 程式碼片段選擇器 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.expansionpicker
helpviewer_keywords:
- Code Snippet Picker
- IntelliSense code snippets, Code Snippet Picker
- code snippets, Code Snippet Picker
ms.assetid: f0862d48-fbbc-4cfe-b228-24492d5c89c4
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 913594f47288715e0050643f365f9225810f6ded
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682357"
---
# <a name="code-snippet-picker"></a>程式碼片段選擇器
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 程式碼編輯器提供了 [程式碼片段選擇器] ，讓您只需按幾下滑鼠即可將現成的程式碼區塊插入至使用中文件。  
  
 顯示 [程式碼片段選擇器] 的程序會根據所使用的語言而有所不同。  
  
- [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] - 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著選取 [插入程式碼片段]。  
  
- [!INCLUDE[csprcs](../../includes/csprcs-md.md)] - 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著按一下 [插入程式碼片段] 或 [範圍陳述式]。  
  
- [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] - 無法使用 [程式碼片段選擇器]。  
  
- Visual F# - 無法使用 [程式碼片段選擇器]。  
  
- [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] -- 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著按一下 [插入程式碼片段] 或 [範圍陳述式]。  
  
- XML - 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著按一下 [插入程式碼片段] 或 [範圍陳述式]。  
  
- HTML - 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著按一下 [插入程式碼片段] 或 [範圍陳述式]。  
  
- SQL - 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著按一下 [插入程式碼片段]。  
  
  在大部分的 Visual Studio 開發語言中，您可以使用 [程式碼片段管理員] 將資料夾新增至 [資料夾清單]，[程式碼片段選擇器] 會掃描那些資料夾中是否有 XML程式碼片段檔案。 您也可以建立自己的程式碼片段並新增至清單。 如需詳細資訊，請參閱[逐步解說：建立程式碼片段](../../ide/walkthrough-creating-a-code-snippet.md)。  
  
## <a name="uielement-list"></a>UIElement 清單  
 項目名稱  
 可編輯的文字欄位，它會顯示 [項目清單] 中已選取項目的名稱。 若要累加搜尋您想要的項目，請在這個欄位開始鍵入項目名稱。 繼續新增字母，直到 [項目清單] 中選取了所需項目為止。  
  
 項目清單  
 可供插入的程式碼片段清單，或是含有程式碼片段的資料夾清單。 若要插入程式碼片段或展開資料夾，請選取您要的項目並按 Enter。  
  
## <a name="see-also"></a>另請參閱  
 [使用程式碼片段的最佳做法](../../ide/best-practices-for-using-code-snippets.md)   
 [Visual Basic IntelliSense 程式碼片段](https://msdn.microsoft.com/library/ffdde4c9-8141-4906-b09b-15181357a643)   
 [在程式碼中設定書籤](../../ide/setting-bookmarks-in-code.md)   
 [如何：使用範圍陳述式程式碼片段](../../ide/how-to-use-surround-with-code-snippets.md)
