---
title: 進階、C#、文字編輯器、選項 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- outlining options [J#]
- XML documentation, creating
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93ddc0af7daecaeb64586d84e210180d7025ad81
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301388"
---
# <a name="options-text-editor-c-advanced"></a>進階、C#、文字編輯器、選項
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
使用這個對話方塊來修改 Visual C# 的編輯器格式、程式碼重構和 XML 文件註解設定。 若要存取這個對話方塊，請按一下 [工具] 功能表上的 [選項]，並依序展開 [文字編輯器] 資料夾和 [C#]，然後按一下 [進階]。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## <a name="outlining"></a>大綱  
 檔案開啟時進入大綱模式  
 選取此選項時，會自動設定程式碼檔的大綱，以建立可摺疊的程式碼區塊。 第一次開啟檔案時，會摺疊 #regions 區塊和非現用程式碼區塊。  
  
## <a name="editor-help"></a>編輯器說明  
 為編輯器中的錯誤加上底線  
 識別程式碼中的建置錯誤。 選取這個選項時，會使用具有特定意義的色彩來顯示波浪底線︰  
  
-   剖析錯誤為紅色。  
  
-   建置錯誤為藍色。  
  
-   建置警告為綠色。  
  
-   無效的[編輯後繼續](../../debugger/edit-and-continue.md)編輯為紫色。  
  
 將指標移至加底線程式碼區段上方，來查看具有錯誤資訊的工具提示。  
  
 顯示即時語意錯誤  
 識別未進行明確編譯的特定編譯錯誤，例如，宣告和使用未知類型，或是參考未知屬性。  
  
 反白顯示游標下的符號參考  
 如果將游標置入符號內，或按一下符號，則會反白顯示該符號在程式碼檔中的所有執行個體。  
  
## <a name="refactoring"></a>重構  
 驗證重構結果  
 如果您嘗試重構包含建置錯誤的程式碼，或重構導致程式碼參考繫結至與其原始繫結不同的項目，則會顯示 [驗證結果] 對話方塊。  
  
 成員具備編譯器產生參考時發出警告  
 當您嘗試重構與編譯器產生參考同名的成員時，會顯示警告對話方塊。  
  
## <a name="xml-documentation-comments"></a>XML 文件註解  
 產生 /// 的 XML 文件註解  
 選取此選項時，會在您輸入 /// 註解簡介之後，自動插入 XML 文件註解的 \<summary> 開始和結束標記。 如需 XML 文件的詳細資訊，請參閱 [XML 文件註解](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)。  
  
## <a name="implement-interface"></a>實作介面  
 以 #region 圍繞產生的程式碼  
 使用 [實作介面] 或 [明確實作介面] 時，在方法周圍插入 #region \<介面名稱> 成員。  
  
## <a name="organize-usings"></a>組合管理 Using  
 排序 using 時先放置 'System' 指示詞  
 選取此選項時，`System` using 指示詞會出現在其他 using 指示詞前面。 如需詳細資訊，請參閱[排序 Using](../../misc/sort-usings.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件註解](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)   
 [設定語言特定編輯器選項](../../ide/reference/setting-language-specific-editor-options.md)   
 [Visual C# IntelliSense](../../ide/visual-csharp-intellisense.md)



