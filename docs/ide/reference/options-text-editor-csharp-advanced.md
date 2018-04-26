---
title: 進階、C#、文字編輯器、選項
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- XML documentation, creating
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a7675d711a4a1df6af4643a459f49b6ef518e5b4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="options-text-editor-c-advanced"></a>進階、C#、文字編輯器、選項

使用 [進階] 選項頁面來修改 C# 的編輯器格式、程式碼重構和 XML 文件註解設定。 若要存取此選項頁面，請選擇 [工具] > [選項]，然後選擇 [文字編輯器] > [C#] > [進階]。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。

## <a name="analysis"></a>分析

- 啟用完整解決方案分析

   除了開啟程式碼檔案之外，您也必須為解決方案中的所有檔案啟用程式法分析。 如需詳細資訊，請參閱[完整解決方案分析](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)。

- 在外部處理序中執行編輯器功能分析 (實驗性)

## <a name="using-directives"></a>using 指示詞

- 排序 using 時先放置 'System' 指示詞

- 使用指示詞群組來進行分隔

- 為參考組件中的類型建議 Using

- 為 NuGet 套件中的類型建議 Using

## <a name="highlighting"></a>醒目提示

- 反白顯示游標下的符號參考

   如果將游標置入符號內，或按一下符號，則會反白顯示該符號在程式碼檔中的所有執行個體。

- 醒目提示游標下的相關關鍵字

## <a name="outlining"></a>大綱

- 檔案開啟時進入大綱模式

   選取此選項時，會自動設定程式碼檔的大綱，以建立可摺疊的程式碼區塊。 第一次開啟檔案時，會摺疊 #regions 區塊和非現用程式碼區塊。

- 顯示程序行分隔符號

- 顯示宣告層級建構的大綱

- 顯示程式碼層級建構的大綱

- 顯示註解及前置處理器區域的大綱

- 在摺疊至定義時摺疊 #region

## <a name="fading"></a>淡出

- 淡出未使用的 Using

- 淡出執行不到的指令碼

## <a name="block-structure-guides"></a>區塊結構輔助線

- 顯示宣告層級建構的輔助線

- 顯示程式碼層級建構的輔助線

## <a name="editor-help"></a>編輯器說明

- 產生 /// 的 XML 文件註解

   選取此選項時，會在您鍵入 `///` 註解簡介後插入 XML 文件註解的 XML 元素。 如需有關 XML 文件的詳細資訊，請參閱 [XML 文件註解 (C# 程式設計指南)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)。

- 在寫入 /\* \*/ 註解時，於新行開頭插入 \*)

- 顯示重新命名追蹤的預覽

- 按下 Enter 時分隔字串常值

- 回報 'string.Format' 呼叫中的無效預留位置

## <a name="extract-method"></a>擷取方法

- 不要在自訂結構上放置 ref 及 out

## <a name="implement-interface-or-abstract-class"></a>實作介面或抽象類別

- 當插入屬性、事件及方法時，將其與其他相同種類成員放在一起或結尾

- 當產生屬性時，偏好 throwing 屬性或 auto 屬性

## <a name="see-also"></a>另請參閱

- [如何：在文件產生中插入 XML 註解](../../ide/reference/generate-xml-documentation-comments.md)
- [XML 文件註解 (C# 程式設計手冊)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [使用 XML 註解記錄您的程式碼 (C# 指南)](/dotnet/csharp/codedoc)
- [設定語言特定編輯器選項](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)