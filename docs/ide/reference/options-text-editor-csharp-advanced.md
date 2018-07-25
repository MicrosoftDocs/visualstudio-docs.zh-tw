---
title: 進階、C#、文字編輯器、選項
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: ab08de0c6993f57c719f69ccf27e30e3cbe41c32
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433298"
---
# <a name="options-text-editor-c-advanced"></a>進階、C#、文字編輯器、選項

使用 [進階] 選項頁面來修改 C# 的編輯器格式、程式碼重構和 XML 文件註解設定。 若要存取此選項頁面，請選擇 [工具] > [選項]，然後選擇 [文字編輯器] > [C#] > [進階]。

> [!NOTE]
> 並非所有選項都會列在此處。

## <a name="analysis"></a>分析

- 啟用完整解決方案分析

   除了開啟程式碼檔案之外，您也必須為解決方案中的所有檔案啟用程式法分析。 如需詳細資訊，請參閱[完整解決方案分析](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)。

## <a name="highlighting"></a>醒目提示

- 反白顯示游標下的符號參考

   如果將游標置入符號內，或按一下符號，則會反白顯示該符號在程式碼檔中的所有執行個體。

## <a name="outlining"></a>大綱

- 檔案開啟時進入大綱模式

   選取此選項時，會自動設定程式碼檔的大綱，以建立可摺疊的程式碼區塊。 第一次開啟檔案時，會摺疊 #regions 區塊和非現用程式碼區塊。

## <a name="editor-help"></a>編輯器說明

- 產生 /// 的 XML 文件註解

   選取此選項時，會在您鍵入 `///` 註解簡介後插入 XML 文件註解的 XML 元素。 如需有關 XML 文件的詳細資訊，請參閱 [XML 文件註解 (C# 程式設計指南)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)。

## <a name="see-also"></a>另請參閱

- [如何：在文件產生中插入 XML 註解](../../ide/reference/generate-xml-documentation-comments.md)
- [XML 文件註解 (C# 程式設計手冊)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [使用 XML 註解記錄您的程式碼 (C# 指南)](/dotnet/csharp/codedoc)
- [設定語言專用編輯器的選項](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)