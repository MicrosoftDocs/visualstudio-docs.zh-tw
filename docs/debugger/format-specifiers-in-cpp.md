---
title: 偵錯工具中的格式規範 (c + +) |Microsoft 檔
description: 使用格式規範來變更在 [監看式]、[自動變數] 或 [區域變數] 視窗中顯示值的格式。 本文提供使用詳細資料。
ms.custom: SEO-VS-2020
ms.date: 3/11/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- C++
helpviewer_keywords:
- QuickWatch dialog box, format specifiers in C++
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- expressions [C++], format specifiers
- specifiers, watch variable format
- specifiers
- Watch window, format specifiers in C++
- watch variable symbols
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 0f6f3b7c-ce2c-4b4d-b14f-7589dbed5444
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 2a3fa99594f42e7e9c3739a8a8d57abf226bc04c
ms.sourcegitcommit: 66951f064d601b1d7a2253cb9b250380807e12db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2021
ms.locfileid: "103483189"
---
# <a name="format-specifiers-for-c-in-the-visual-studio-debugger"></a>Visual Studio 偵錯工具中 c + + 的格式規範

您可以使用格式規範變更在 [**監看式]、[** 自動變數]**和 [****區域變數**] 視窗中顯示值的格式。

您也可以 **在 [即時** 運算] 視窗、 **命令** 視窗、追蹤 [點](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)，甚至是在來源視窗中使用格式規範。 如果您在這些視窗中的運算式上暫停，結果會顯示在 [資料提示](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)中。 DataTip 顯示會反映格式規範。

> [!NOTE]
> 當 Visual Studio 原生偵錯工具變更為新的偵錯工具引擎時，會加入一些新的格式規範，並移除一些舊的格式規範。 當您使用 C++/CLI 執行 Interop (混合原生和 Managed) 偵錯時仍會使用較舊的偵錯工具。

## <a name="set-format-specifiers"></a>設定格式規範

我們將使用下列範例程式碼：

```C++
int main() {
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

將 `my_var1` 變數加入至 [**監看** 式] 視窗（在進行調試時），並將它設為 [ **Debug**  >  ****]  >    >   接下來，以滑鼠右鍵按一下變數，然後選取 [ **十六進位顯示**]。 現在 [ **監看** 式] 視窗會顯示值0x0065。 若要查看以字元而非整數表示的此值，請先以滑鼠右鍵按一下並取消選取 [ **十六進位顯示**]。 然後在 **名稱** 資料行中 **，** 將字元格式規範 c 加入變數名稱後面。 **值** 資料行現在會顯示 **101 ' e '**。

![Visual Studio 監看式視窗的螢幕擷取畫面，其中有一個選取的線條顯示 my_var1，其值為 101 ' e ' 和 int 類型。](../debugger/media/watchformatcplus1.png)

::: moniker range=">= vs-2019" 
您可以在 [ **監看** 式] 視窗中附加逗號 (，) ，以從可用的格式規範清單中查看並選取。 

![WatchFormatSpecDropdown](../debugger/media/vs-2019/format-specs-cpp.png "FormatSpecCpp")

::: moniker-end

## <a name="format-specifiers"></a><a name="BKMK_Visual_Studio_2012_format_specifiers"></a> 格式規範

下表說明您可以在 Visual Studio 中使用的格式規範。 只有新的偵錯工具才支援粗體的規範，而不支援以 c + +/CLI 進行 interop 偵錯工具

::: moniker range=">= vs-2019" 

|規範|格式|原始的監看值|顯示的值|
|---------------|------------|--------------------------|---------------------|
|d|十進位整數|0x00000066|102|
|o|不帶正負號的八進位整數|0x00000066|000000000146|
|x<br /><br /> **h**|十六進位整數|102|0xcccccccc|
|X<br /><br /> **H**|十六進位整數|102|0xcccccccc|
|xb<br /><br /> **Hb**|十六進位整數 (沒有前置的 0x)|102|cccccccc|
|Xb<br /><br /> **Hb**|十六進位整數 (沒有前置的 0x)|102|CCCCCCCC|
|b|不帶正負號的二進位整數|25|0b00000000000000000000000000011001|
|bb|不帶正負號的二進位整數 (不含前置的 0b)|25|00000000000000000000000000011001|
|e|科學記號標記法|25000000|2.500000e+07|
|g|科學記號或浮點數中較短者|25000000|2.5e+07|
|c|單一字元|0x0065|101 'e'|
|s|以引號括住的 const char * 字串 () |\<location> "hello world"|"hello world"|
|**某人**|const char* 字串 (無引號)|\<location> "hello world"|hello world|
|s8|UTF-8 字串|\<location> 「這是 UTF-8 咖啡杯̃•」|「這是 UTF-8 咖啡杯☕」|
|**s8b**|Utf-8 字串 (無引號)|\<location> "hello world"|hello world|
|su|Unicode (UTF-16 編碼) 字串 (加上引號) |\<location> L "hello world"|L"hello world"<br /><br /> u"hello world"|
|sub|Unicode (UTF-16 編碼) 字串 (無引號)|\<location> L "hello world"|hello world|
|bstr|以引號括住的 BSTR 二進位字串 () |\<location> L "hello world"|L"hello world"|
|env|環境區塊 (雙重 null 結尾的字串)|\<location>L "=：： =：： \\ \\ "|L "=：： =：： \\ \\ \\ 0 = c： = c： \\ \\ windows \\ \\ system32 \\ 0ALLUSERSPROFILE = .。。|
|**s32**|以引號括住32的 UTF-8 字串 () |\<location> U "hello world"|u"hello world"|
|**s32b**|Utf-32 字串 (沒有引號)|\<location> U "hello world"|hello world|
|**en**|列舉|Saturday(6)|星期六|
|**hv**|指標類型：指出檢查中的指標值是陣列堆積配置的結果，例如 `new int[3]`。|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**那**|隱藏物件指標的記憶體位址。|\<location>，{member = value ...}|{成員=值...}|
|**nd**|只顯示基底類別資訊，忽略衍生類別|`(Shape*) square` 包含基底類別和衍生類別資訊|只顯示基底類別資訊|
|小時|HRESULT 或 Win32 錯誤碼。 當偵錯工具自動將其解碼時，Hresult 不再需要這個規範。|S_OK|S_OK|
|wc|Window 類別旗標|0x0010|WC_DEFAULTCHAR|
|wm|Windows 訊息編號|16|WM_CLOSE|
|nr|隱藏「未經處理的檢視」項目|
|nvo|只顯示數值的「原始視圖」專案|
|!|未經處理格式，忽略任何資料類型檢視自訂|\<customized representation>|4|

::: moniker-end

::: moniker range="vs-2017" 

|規範|格式|原始的監看值|顯示的值|
|---------------|------------|--------------------------|---------------------|
|d|十進位整數|0x00000066|102|
|o|不帶正負號的八進位整數|0x00000066|000000000146|
|x<br /><br /> **h**|十六進位整數|102|0xcccccccc|
|X<br /><br /> **H**|十六進位整數|102|0xcccccccc|
|c|單一字元|0x0065, c|101 'e'|
|s|以引號括住的 const char * 字串 () |\<location> "hello world"|"hello world"|
|**某人**|const char* 字串 (無引號)|\<location> "hello world"|hello world|
|s8|UTF-8 字串|\<location> 「這是 UTF-8 咖啡杯̃•」|「這是 UTF-8 咖啡杯☕」|
|**s8b**|Utf-8 字串 (無引號)|\<location> "hello world"|hello world|
|su|Unicode (UTF-16 編碼) 字串 (加上引號) |\<location> L "hello world"|L"hello world"<br /><br /> u"hello world"|
|sub|Unicode (UTF-16 編碼) 字串 (無引號)|\<location> L "hello world"|hello world|
|bstr|以引號括住的 BSTR 二進位字串 () |\<location> L "hello world"|L"hello world"|
|env|環境區塊 (雙重 null 結尾的字串)|\<location>L "=：： =：： \\ \\ "|L "=：： =：： \\ \\ \\ 0 = c： = c： \\ \\ windows \\ \\ system32 \\ 0ALLUSERSPROFILE = .。。|
|**s32**|以引號括住32的 UTF-8 字串 () |\<location> U "hello world"|u"hello world"|
|**s32b**|Utf-32 字串 (沒有引號)|\<location> U "hello world"|hello world|
|**en**|列舉|Saturday(6)|星期六|
|**hv**|指標類型：指出檢查中的指標值是陣列堆積配置的結果，例如 `new int[3]`。|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**那**|隱藏物件指標的記憶體位址。|\<location>，{member = value ...}|{成員=值...}|
|**nd**|只顯示基底類別資訊，忽略衍生類別|`(Shape*) square` 包含基底類別和衍生類別資訊|只顯示基底類別資訊|
|小時|HRESULT 或 Win32 錯誤碼。 當偵錯工具自動將其解碼時，Hresult 不再需要這個規範。|S_OK|S_OK|
|wc|Window 類別旗標|0x0010|WC_DEFAULTCHAR|
|wm|Windows 訊息編號|16|WM_CLOSE|
|!|未經處理格式，忽略任何資料類型檢視自訂|\<customized representation>|4|

::: moniker-end

> [!NOTE]
> 當 **hv** 格式規範出現時，偵錯工具會嘗試判斷緩衝區的長度，並顯示該元素的數目。 因為偵錯工具不一定能一直找到陣列確切的緩衝區大小，所以您應該盡可能使用大小規範 `(pBuffer,[bufferSize])` 。 當緩衝區大小不是可供使用時， **hv** 格式規範會很有用。

### <a name="size-specifiers-for-pointers-as-arrays"></a><a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> 做為陣列的指標大小規範

如果您希望將物件指標視為陣列，可以使用整數或運算式來指定陣列項目的數量。

|規範|格式|原始的監看值|顯示的值|
|---------------|------------|---------------------------|---------------------|
|n|十進位或 **十六進位** 整數|pBuffer,[32]<br /><br /> pBuffer,**[0x20]**|顯示 `pBuffer` 為 32 個項目的陣列。|
|**exp**|判斷值為整數的有效 C++ 運算式。|pBuffer,[bufferSize]|PBuffer 顯示為 `bufferSize` 項目的陣列。|
|**expand(n)**|判斷值為整數的有效 C++ 運算式|pBuffer，expand(2)|顯示  `pBuffer`的第三個項目|

## <a name="format-specifiers-for-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> 使用 C++/CLI 的 Interop 偵錯格式規範

偵錯原生和 C++/CLI 程式碼僅支援 **粗體** 的規範。 這需要使用 [Managed 相容性模式](../debugger/general-debugging-options-dialog-box.md)指定的舊版偵錯工具。

|規範|格式|原始的監看值|顯示的值|
|---------------|------------|--------------------------|---------------------|
|**d**<br /><br />**i**|帶正負號的十進位整數|0xF000F065|-268373915|
|**u**|不帶正負號的十進位整數|0x0065|101|
|o|不帶正負號的八進位整數|0xF065|0170145|
|x<br /><br />X|十六進位整數|61541|0x0000f065|
|**l**<br /><br />**h**|長整數或短整數前置詞，用於：d、i、u、o、x、X|00406042|0x0c22|
|**f**|帶正負號的浮點數|(3./2.), f|1.500000|
|**pci-e**|帶正負號的科學記號表示法|(3.0/2.0)|1.500000e+000|
|**G**|帶正負號的浮點數或帶正負號的科學記號<br/> 以較短者為准|(3.0/2.0)|1.5|
|c|單一字元|\<location>|101 'e'|
|s|const char * (加上引號) |\<location>|"hello world"|
|su|const wchar_t*<br /><br /> 以引號括住的 const char16_t \* () |\<location>|L"hello world"|
|sub|const wchar_t*<br /><br /> const char16_t\*|\<location>|hello world|
|s8|const char * (加上引號) |\<location>|"hello world"|
|小時|HRESULT 或 Win32 錯誤碼。<br/>當偵錯工具自動將其解碼時，Hresult 不再需要這個規範。|S_OK|S_OK|
|wc|Window 類別旗標|0x00000040,|WC_DEFAULTCHAR|
|wm|Windows 訊息編號|0x0010|WM_CLOSE|
|!|原始格式，忽略任何資料類型視圖自訂|\<customized representation>|4|

### <a name="format-specifiers-for-memory-locations-in-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> 使用 c + +/CLI 進行 interop 偵錯工具中記憶體位置的格式規範

下表描述用於記憶體位置的格式化符號。 您可將記憶體位置規範用於評估結果為位置的任何數值或運算式。

偵錯原生和 C++/CLI 程式碼僅支援 **粗體** 的規範。 這需要使用 [Managed 相容性模式](../debugger/general-debugging-options-dialog-box.md)指定的舊版偵錯工具。

|符號|格式|原始的監看值|顯示的值|
|------------|------------|--------------------------|---------------------|
|**馬**|64 個 ASCII 字元|0x0012ffac|0x0012ffac .4...0...".0W&.......1W&.0.:W..1...."..1.JO&.1.2.."..1...0y....1|
|**m**|十六進位表示的 16 個位元組，後面跟著 16 個 ASCII 字元|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|
|**M b**|十六進位表示的 16 個位元組，後面跟著 16 個 ASCII 字元|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|
|**M w**|8 個字組|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|
|**md**|4 個 Doubleword|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|
|**Mq**|2 個 Quadword|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|
|**木**|2 個位元組的字元 (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|

### <a name="size-specifier-for-pointers-as-arrays-in-interop-debugging-with-ccli"></a><a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> 在使用 C++/CLI 的 Interop 偵錯中作為陣列之指標的大小規範

如果您希望將物件指標視為陣列，可以使用整數來指定陣列項目的數量。

|規範|格式|運算式|顯示的值|
|---------------|------------|----------------|---------------------|
|n|十進位整數|pBuffer[32]|顯示 `pBuffer` 為 32 個項目的陣列。|