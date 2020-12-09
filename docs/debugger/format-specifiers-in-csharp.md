---
title: '偵錯工具中的格式規範 (c # ) |Microsoft Docs'
description: 使用格式規範來變更監看式視窗中顯示值的格式。 本文提供使用詳細資料。
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 31739b9c8fecc862c891173a792986b467730400
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862785"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Visual Studio 偵錯工具中 c # 的格式規範
您可以使用格式規範變更在 [ **監看** 式] 視窗中顯示值的格式。 您也可以 **在 [即時** 運算] 視窗、 **命令** 視窗、追蹤 [點](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)和來源視窗中使用格式規範。 如果您在這些視窗中的運算式上暫停，結果會以指定的格式顯示顯示在  [資料提示](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) 中。

若要使用格式規範，請輸入變數運算式，並在後面加上逗號和適當的規範。

## <a name="set-format-specifiers"></a>設定格式規範
我們將使用下列範例程式碼：

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

將 `my_var1` 變數加入至 [**監看** 式] 視窗（在進行調試時），並將它設為 [ **Debug**  >  ****]  >  **Watch**  >  **Watch 1** 接下來，以滑鼠右鍵按一下變數，然後選取 [ **十六進位顯示**]。 現在 [ **監看** 式] 視窗會顯示值0x0065。 若要以十進位整數而非十六進位整數來查看此值，請在變數名稱後面的 **名稱** 資料行中，加入十進位格式規範 **d** 。 **值** 資料行現在會顯示 **101**。

![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")

::: moniker range=">= vs-2019" 

您可以在 [ **監看** 式] 視窗中附加逗號 (，) ，以從可用的格式規範清單中查看並選取。 

![FormatSpecCSharp](../debugger/media/vs-2019/format-specs-csharp.png "FormatSpecCSharp")

::: moniker-end

## <a name="format-specifiers"></a>格式規範
下表描述 Visual Studio 偵錯工具的 c # 格式規範。

|規範|格式|原始的監看值|顯示|
|---------------|------------|--------------------------|--------------|
|ac|強制評估運算式，這在隱含評估屬性和隱含函式呼叫關閉時很有用。|訊息「使用者已關閉隱含函式評估」|\<value>|
|d|十進位整數|0x0065|101|
|動態|使用動態檢視顯示指定的物件|顯示物件所有成員，包括動態檢視|只顯示動態檢視|
|h|十六進位整數|61541|0x0000F065|
|nq|沒有引號的字串|"My String"|My String|
|Nse|指定行為，而不是格式。 使用「沒有副作用」來評估運算式。 如果無法解讀運算式，而且只能由評估 (（例如函式呼叫) ）解析，則會改為看到錯誤。|N/A|N/A|
|隱藏|顯示所有公用及非公用成員|顯示公用成員|顯示所有成員|
|raw|以項目在原始項目節點中出現的形式顯示該項目。 只有在 Proxy 物件上有效。|字典\<T>|字典的原始觀點\<T>|
|results|與實作為 IEnumerable 或 IEnumerable 之型別的變數搭配使用 \<T> ，通常是查詢運算式的結果。 只顯示包含查詢結果的成員。|顯示所有成員|顯示符合查詢條件的成員|

## <a name="see-also"></a>另請參閱
- [觀賞和快速監看式視窗](../debugger/watch-and-quickwatch-windows.md)
- [自動變數和區域變數視窗](../debugger/autos-and-locals-windows.md)
