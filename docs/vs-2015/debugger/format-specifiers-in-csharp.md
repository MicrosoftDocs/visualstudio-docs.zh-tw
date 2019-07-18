---
title: Format Specifiers in C# |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- CSharp
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
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6085ba95d3880417e517530069734052741113e2
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682494"
---
# <a name="format-specifiers-in-c"></a>在 C 中的格式規範\#

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用格式規範變更在 **監看式** 視窗中顯示值的格式。 您也可以在 [即時運算]  視窗、[命令]  視窗，甚至來源視窗中使用格式規範。 如果暫停在這些視窗中的某個運算式上，結果則會顯示在 DataTip (資料提示方塊)。 DataTip (資料提示方塊) 會反映 DataTip 顯示中的格式規範。

如要使用格式規範，請輸入運算式且後面加上逗號。 在逗號後面加上適當的規範。

## <a name="using-format-specifiers"></a>使用格式規範

如果您有下列程式碼：

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

將 `my_var1` 變數加入監看式視窗 (偵錯時， **偵錯 / Windows / 監看式 / 監看式 1**) 並將顯示設定為十六進位 (在 **監看式** 視窗中，以滑鼠右鍵按一下變數，然後選取 [十六進位顯示] )。 現在 **監看式** 視窗顯示它包含了值 0x0065。 若希望以十進位整數、非十六進位整數表示這個值，請在 [名稱] 欄位的變數名稱後面，加入十進位格式規範： **, d**。 [值] 欄位現在會顯示十進位值 101

![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")

## <a name="format-specifiers"></a>格式規範

下表說明偵錯工具可辨識的 C# 格式規範。

|指定名稱|格式|原始的監看值|顯示|
|---------------|------------|--------------------------|--------------|
|ac|強制評估運算式。 在隱含評估屬性和隱含函式呼叫關閉時，這就會很有用。 請參閱 [Side Effects and Expressions](https://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e)。|訊息「使用者已關閉隱含函式評估」|\<值>|
|d|十進位整數|0x0065|101|
|動態|使用動態檢視顯示指定的物件|顯示物件所有成員，包括動態檢視|只顯示動態檢視|
|h|十六進位整數|61541|0x0000F065|
|nq|沒有引號的字串|"My String"|My String|
|隱藏|顯示所有公用及非公用成員|顯示公用成員|顯示所有成員|
|raw|以項目在原始項目節點中出現的形式顯示該項目。 只有在 Proxy 物件上有效。|字典\<T >|字典的未經處理檢視\<T >|
|結果|搭配實作 IEnumerable 或 IEnumerable 型別的變數\<T >，通常是查詢運算式的結果。 只顯示包含查詢結果的成員。|顯示所有成員。|顯示符合查詢條件的成員。|

## <a name="see-also"></a>另請參閱

- [監看式及快速監看式視窗](../debugger/watch-and-quickwatch-windows.md)
- [變數視窗](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)
