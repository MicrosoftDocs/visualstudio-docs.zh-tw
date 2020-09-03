---
title: 進階、C#、文字編輯器、選項 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f2d11e78c2402a6541bc87748ed6ba348ba80fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662325"
---
# <a name="options-text-editor-c-advanced"></a>進階、C#、文字編輯器、選項
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用這個對話方塊來修改 Visual C# 的編輯器格式、程式碼重構和 XML 文件註解設定。 若要存取這個對話方塊，請按一下 [工具]**** 功能表上的 [選項]****，並依序展開 [文字編輯器]**** 資料夾和 [C#]****，然後按一下 [進階]****。

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更您的設定，請在 [工具]**** 功能表上選擇 [匯入和匯出設定]****。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。

## <a name="outlining"></a>大綱
 當檔案在選取時開啟時進入大綱模式，會自動概述程式碼檔案，該檔案會建立可折迭的程式碼區塊。 第一次開啟檔案時，會摺疊 #regions 區塊和非現用程式碼區塊。

## <a name="editor-help"></a>編輯器說明
 編輯器中的底線錯誤會識別程式碼中的組建錯誤。 選取這個選項時，會使用具有特定意義的色彩來顯示波浪底線︰

- 剖析錯誤為紅色。

- 建置錯誤為藍色。

- 建置警告為綠色。

- 無效的[編輯後繼續](../../debugger/edit-and-continue.md)編輯為紫色。

  將指標移至加底線程式碼區段上方，來查看具有錯誤資訊的工具提示。

  顯示即時語意錯誤指出沒有明確編譯的特定編譯錯誤，例如，宣告和使用未知的類型或參考未知的屬性。

  當游標位於符號內部或當您按一下符號時，反白顯示資料指標下的符號參考時，會反白顯示該符號在程式碼檔案中的所有實例。

## <a name="refactoring"></a>重構
 當您嘗試重構包含組建錯誤的程式碼時，或重構會導致程式碼參考系結至與原始系結不同的內容時，請確認重構的結果會顯示 [ **驗證結果** ] 對話方塊。

 當您嘗試重構的成員與編譯器產生的參考名稱相同時，在具有編譯器產生之參考的成員上發出警告時，會顯示警告對話方塊。

## <a name="xml-documentation-comments"></a>XML 文件註解
 若已選取，請產生///的 XML 檔批註， \<summary> 並在您輸入///批註簡介之後，自動插入 xml 檔批註的開始和結束標記。 如需 XML 文件的詳細資訊，請參閱 [XML 文件註解](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)。

## <a name="implement-interface"></a>實作介面
 使用時，將產生的程式碼括住 #region \<*interface name*> 在使用實介面或明確執行介面時，在方法周圍插入 #region 成員。

## <a name="organize-usings"></a>組合管理 Using
 先放置 ' System ' 指示詞，並在選取時排序 using，使用指示詞 `System` 會出現在其他 using 指示詞之前。 如需詳細資訊，請參閱[排序 Using](../../misc/sort-usings.md)。

## <a name="see-also"></a>另請參閱
 [XML 檔批註](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)[設定語言特定編輯器選項](../../ide/reference/setting-language-specific-editor-options.md) [Visual c # IntelliSense](../../ide/visual-csharp-intellisense.md)
