---
title: 格式規範，在偵錯工具 （c + +） |Microsoft Docs
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 8ad821c15ee8b405982d36c6b1c62d038bb11633
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227718"
---
# <a name="format-specifiers-for-c-in-the-visual-studio-debugger"></a>C + + 的 Visual Studio 偵錯工具中的格式規範
您可以變更在顯示值的格式**監看式**視窗使用格式規範。

您也可以使用中的格式規範**Immediate**  視窗中，**命令**視窗中[追蹤點](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)，和甚至來源視窗中。 如果您暫停在這些視窗中的運算式，結果會出現在[DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)。 DataTip 顯示會反映格式規範。

> [!NOTE]
> 當 Visual Studio 原生偵錯工具變更為新的偵錯引擎中時，新增一些新的格式規範，並已移除一些舊的。 當您使用 C++/CLI 執行 Interop (混合原生和 Managed) 偵錯時仍會使用較舊的偵錯工具。

## <a name="set-format-specifiers"></a>設定格式規範
我們將使用下列的範例程式碼：

```C++
int main() {
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

新增`my_var1`變數設為**監看式**偵錯時，視窗**偵錯** > **Windows** > **觀看** > **監看式 1**。 接下來，以滑鼠右鍵按一下變數，然後選取**十六進位顯示**。 現在**監看式**視窗會顯示了值 0x0065。 若要查看為一個字元，而不是整數，表示這個值，第一次上按一下滑鼠右鍵，然後取消選取**十六進位顯示**。 然後加入字元格式規範 **、 c**中**名稱**的變數名稱後面的資料行。 **值**資料行現在會顯示**101 'e'**。

![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")

## <a name="BKMK_Visual_Studio_2012_format_specifiers"></a> 格式規範
下表描述您可以使用 Visual Studio 中的格式規範。 以粗體顯示的規範才支援新的偵錯工具，而非 interop 偵錯使用 C + + /cli CLI。

|指定名稱|格式|原始的監看值|顯示的值|
|---------------|------------|--------------------------|---------------------|
|d|十進位整數|0x00000066|102|
|o|不帶正負號的八進位整數|0x00000066|000000000146|
|x<br /><br /> **h**|十六進位整數|102|0xcccccccc|
|X<br /><br /> **H**|十六進位整數|102|0xcccccccc|
|c|單一字元|0x0065, c|101 'e'|
|秒|const char * 字串 （含引號）|\<位置 >"hello world"|"hello world"|
|**sb**|const char* 字串 (無引號)|\<位置 >"hello world"|hello world|
|s8|UTF-8 字串|\<位置 >"This is utf-8 咖啡杯 â˜•"|"This is utf-8 咖啡杯 ☕"|
|**s8b**|Utf-8 字串 (無引號)|\<位置 >"hello world"|hello world|
|su|Unicode （utf-16 編碼） 字串 （含引號）|\<位置> L"hello world"|L"hello world"<br /><br /> u"hello world"|
|sub|Unicode (UTF-16 編碼) 字串 (無引號)|\<位置> L"hello world"|hello world|
|bstr|BSTR 二進位字串 （含引號）|\<位置> L"hello world"|L"hello world"|
|env|環境區塊 (雙重 null 結尾的字串)|\<位置 > L"=:: =::\\\\"|L"=:: =::\\\\\\0 = C: = C:\\\\windows\\\\system32\\0ALLUSERSPROFILE =...|
|**s32**|UTF-32 字串 （含引號）|\<位置 > U"hello world"|u"hello world"|
|**s32b**|Utf-32 字串 (沒有引號)|\<位置 > U"hello world"|hello world|
|**en**|enum|Saturday(6)|星期六|
|**hv**|指標類型：指出檢查中的指標值是陣列堆積配置的結果，例如 `new int[3]`。|\<位置>{\<第一個成員>}|\<位置 > {\<第一個成員 >，\<第二個成員 >，...}|
|**na**|隱藏物件指標的記憶體位址。|\<位置>，{成員=值...}|{成員=值...}|
|**nd**|只顯示基底類別資訊，忽略衍生類別|`(Shape*) square` 包含基底類別和衍生類別資訊|只顯示基底類別資訊|
|hr|HRESULT 或 Win32 錯誤碼。 這個規範不再需要的 Hresult 為偵錯工具自動解碼它們。|S_OK|S_OK|
|wc|Window 類別旗標|0x0010|WC_DEFAULTCHAR|
|wm|Windows 訊息編號|16|WM_CLOSE|
|!|未經處理格式，忽略任何資料類型檢視自訂|\<自訂的表示>|4|

> [!NOTE]
> 當**hv**格式規範出現時，偵錯工具會嘗試判斷緩衝區的長度並顯示該數字的項目。 因為偵錯工具不一定能一直找到陣列確切的緩衝區大小，所以您應該盡可能使用大小規範 `(pBuffer,[bufferSize])` 。 **Hv**格式規範時，適合的緩衝區大小不是隨手可得

### <a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> 做為陣列的指標大小規範
如果您希望將物件指標視為陣列，可以使用整數或運算式來指定陣列項目的數量。

|指定名稱|格式|原始的監看值|顯示的值|
|---------------|------------|---------------------------|---------------------|
|n|十進位或 **十六進位** 整數|pBuffer,[32]<br /><br /> pBuffer,**[0x20]**|顯示 `pBuffer` 為 32 個項目的陣列。|
|**[exp]**|判斷值為整數的有效 C++ 運算式。|pBuffer,[bufferSize]|PBuffer 顯示為 `bufferSize` 項目的陣列。|
|**expand(n)**|判斷值為整數的有效 C++ 運算式|pBuffer，expand(2)|顯示  `pBuffer`的第三個項目|

## <a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> 使用 C++/CLI 的 Interop 偵錯格式規範
偵錯原生和 C++/CLI 程式碼僅支援 **粗體** 的規範。

|指定名稱|格式|原始的監看值|顯示的值|
|---------------|------------|--------------------------|---------------------|
|**d**<br /><br />**i**|帶正負號的十進位整數|0xF000F065|-268373915|
|**u**|不帶正負號的十進位整數|0x0065|101|
|o|不帶正負號的八進位整數|0xF065|0170145|
|x<br /><br />X|十六進位整數|61541|0x0000f065|
|**l**<br /><br />**h**|長整數或短整數前置詞，用於：d、i、u、o、x、X|00406042|0x0c22|
|**f**|帶正負號的浮點數|(3./2.), f|1.500000|
|**e**|帶正負號的科學記號表示法|(3.0/2.0)|1.500000e+000|
|**g**|帶正負號的浮點數或帶正負號的科學記號標記法<br/> 何者較短|(3.0/2.0)|1.5|
|c|單一字元|\<位置>|101 'e'|
|秒|const char * （加上引號）|\<位置>|"hello world"|
|su|const wchar_t*<br /><br /> const char16_t\* （加上引號）|\<位置>|L"hello world"|
|sub|const wchar_t*<br /><br /> const char16_t\*|\<位置>|hello world|
|s8|const char * （加上引號）|\<位置>|"hello world"|
|hr|HRESULT 或 Win32 錯誤碼。<br/>這個規範不再需要的 Hresult 為偵錯工具自動解碼它們。|S_OK|S_OK|
|wc|Window 類別旗標|0x00000040,|WC_DEFAULTCHAR|
|wm|Windows 訊息編號|0x0010|WM_CLOSE|
|!|未經處理的格式，並忽略任何資料類型檢視自訂項目|\<自訂的表示>|4|

### <a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> 格式規範的記憶體位置在 interop 偵錯使用 C + + /cli CLI
下表描述用於記憶體位置的格式化符號。 您可將記憶體位置規範用於評估結果為位置的任何數值或運算式。

|符號|格式|原始的監看值|顯示的值|
|------------|------------|--------------------------|---------------------|
|**ma**|64 個 ASCII 字元|0x0012ffac|0x0012ffac .4...0...".0W&.......1W&.0.:W..1...."..1.JO&.1.2.."..1...0y....1|
|**m**|十六進位表示的 16 個位元組，後面跟著 16 個 ASCII 字元|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|
|**mb**|十六進位表示的 16 個位元組，後面跟著 16 個 ASCII 字元|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|
|**mw**|8 個字組|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|
|**md**|4 個 Doubleword|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|
|**mq**|2 個 Quadword|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|
|**mu**|2 個位元組的字元 (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|

### <a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> 在使用 C++/CLI 的 Interop 偵錯中作為陣列之指標的大小規範
如果您希望將物件指標視為陣列，可以使用整數來指定陣列項目的數量。

|指定名稱|格式|運算式|顯示的值|
|---------------|------------|----------------|---------------------|
|n|十進位整數|pBuffer[32]|顯示 `pBuffer` 為 32 個項目的陣列。|
