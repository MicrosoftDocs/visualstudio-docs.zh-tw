---
title: 進階、C#、文字編輯器、選項
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d1d540f3a49eda22973b25a6b9a91691907efe93
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666282"
---
# <a name="options-text-editor-c-advanced"></a>進階、C#、文字編輯器、選項

使用 [進階] 選項頁面來修改 C# 的編輯器格式、程式碼重構和 XML 文件註解設定。 若要存取此選項頁面，請選擇 [工具] > [選項]，然後選擇 [文字編輯器] > [C#] > [進階]。

> [!NOTE]
> 並非所有選項都會列在此處。

## <a name="analysis"></a>分析

- 啟用完整解決方案分析

   除了開啟程式碼檔案之外，您也必須為解決方案中的所有檔案啟用程式法分析。 如需詳細資訊，請參閱[完整解決方案分析](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)。

## <a name="using-directives"></a>using 指示詞

- 排序 using 時先放置 'System' 指示詞

   選取後，快顯功能表中的 [移除並排序 Using] 命令會對 `using` 指示詞進行排序，並將 'System' 命名空間置於清單頂端。

   排序之前：

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   排序之後：

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using AutoMapper;
   using FluentValidation;
   using Newtonsoft.Json;
   ```

- 使用指示詞群組來進行分隔

   選取後，快顯功能表中的 [移除並排序 Using] 命令會透過在具有相同根命名空間的指示詞群組之間插入空白行來分隔 `using` 指示詞。

   排序之前：

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   排序之後：

   ```csharp
   using AutoMapper;

   using FluentValidation;

   using Newtonsoft.Json;

   using System;
   using System.Collections.Generic;
   using System.Linq;
   ```

- 為參考組件中的類型建議 Using
- 為 NuGet 套件中的類型建議 Using

   選取這些選項後，[快速動作](../quick-actions.md)可用來安裝 NuGet 套件，並為未參考的類型新增 `using` 指示詞。

   ![在 Visual Studio 中安裝 NuGet 套件的快速動作](media/nuget-lightbulb.png)

## <a name="highlighting"></a>醒目提示

- 反白顯示游標下的符號參考

   如果將游標置入符號內，或按一下符號，則會反白顯示該符號在程式碼檔中的所有執行個體。

## <a name="outlining"></a>大綱

- 檔案開啟時進入大綱模式

   選取此選項時，會自動設定程式碼檔的大綱，以建立可摺疊的程式碼區塊。 第一次開啟檔案時，會摺疊 #regions 區塊和非現用程式碼區塊。

- 顯示程序行分隔符號

   文字編輯器會指出程序的可見範圍。 系統會在專案的 *.cs* 原始程式檔中描繪一行，描繪的位置如下表所列：

   |.cs 原始程式檔中的位置|行位置的範例|
   |---------------------------------|------------------------------|
   |在區塊宣告建構關閉之後|-   在類別、結構、模組、介面和列舉的結尾處<br />-   在屬性、函式或子函式之後<br />-   不在屬性中的 get 與 set 子句之間|
   |在一組的單一行建構之後|-   在重要的陳述式之後，類別檔中的型別定義之前<br />-   在類別中宣告的變數之後，任何程序之前|
   |在單一行宣告 (非區塊層級宣告) 之後|-   接在重要的陳述式、繼承陳述式、變數宣告、事件宣告、委派宣告和 DLL 宣告陳述式之後|

## <a name="block-structure-guides"></a>區塊結構輔助線

選取這些核取方塊可在程式碼中的大括號 ( **{}** ) 之間顯示虛線垂直線。 然後，您可以輕鬆查看宣告層級和程式碼層級建構的個別程式碼區塊。

## <a name="editor-help"></a>編輯器說明

- 產生 /// 的 XML 文件註解

   選取此選項時，會在您鍵入 `///` 註解簡介後插入 XML 文件註解的 XML 元素。 如需有關 XML 文件的詳細資訊，請參閱 [XML 文件註解 (C# 程式設計指南)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)。

## <a name="see-also"></a>請參閱

- [如何：在文件產生中插入 XML 註解](../../ide/reference/generate-xml-documentation-comments.md)
- [XML 文件註解 (C# 程式設計手冊)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [使用 XML 註解記錄您的程式碼 (C# 指南)](/dotnet/csharp/codedoc)
- [設定語言專用編輯器的選項](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
