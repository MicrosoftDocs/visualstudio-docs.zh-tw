---
title: 格式規範，偵錯工具 (C#) |Microsoft Docs
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
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: f01951a45a2e50f6dac093924627fe178011c9f0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53899008"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>格式規範，在C#在 Visual Studio 偵錯工具
您可以變更在顯示值的格式**監看式**視窗使用格式規範。 您也可以使用中的格式規範**即時運算** 視窗中，**命令**視窗中[追蹤點](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)，並在來源視窗中。 如果您暫停在這些視窗中的運算式，結果會出現在[DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)中指定的格式顯示。  
  
 若要使用的格式規範，請輸入變數的運算式後面接著一個逗號和適當的規範。  
  
## <a name="set-format-specifiers"></a>設定格式規範  
我們將使用下列的範例程式碼：   
  
```csharp  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 新增`my_var1`變數設為**監看式**偵錯時，視窗**偵錯** > **Windows** > **觀看** > **監看式 1**。 接下來，以滑鼠右鍵按一下變數，然後選取**十六進位顯示**。 現在**監看式**視窗會顯示了值 0x0065。 若要查看此值為十進位整數，而不是十六進位整數，加入十進位格式規範 **，d**中**名稱**的變數名稱後面的資料行。 **值**資料行現在會顯示**101**。   
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>格式規範  
 下表描述C#格式規範，Visual Studio 偵錯工具。  
  
|指定名稱|格式|原始的監看值|顯示|  
|---------------|------------|--------------------------|--------------|  
|ac|強制關閉隱含評估屬性和隱含函式呼叫時很有用的運算式評估。|訊息「使用者已關閉隱含函式評估」|\<值>|  
|d|十進位整數|0x0065|101|  
|動態|使用動態檢視顯示指定的物件|顯示物件所有成員，包括動態檢視|只顯示動態檢視|  
|h|十六進位整數|61541|0x0000F065|  
|nq|沒有引號的字串|"My String"|My String|  
|nse|指定的行為，不是格式。 評估與 「 副作用 」 運算式。 如果運算式無法解譯，而且只可以解析 （例如函式呼叫），評估，您會改為看到錯誤。|N/A|N/A|
|隱藏|顯示所有公用及非公用成員|顯示公用成員|顯示所有成員|  
|raw|以項目在原始項目節點中出現的形式顯示該項目。 只有在 Proxy 物件上有效。|字典\<T >|字典的未經處理檢視\<T >|  
|結果|搭配實作 IEnumerable 或 IEnumerable 型別的變數\<T >，通常是查詢運算式的結果。 只顯示包含查詢結果的成員。|顯示所有成員|顯示符合查詢條件的成員|  
  
## <a name="see-also"></a>另請參閱  
 [監看式及快速監看式視窗](../debugger/watch-and-quickwatch-windows.md)   
 [自動變數和區域變數視窗](../debugger/autos-and-locals-windows.md)
