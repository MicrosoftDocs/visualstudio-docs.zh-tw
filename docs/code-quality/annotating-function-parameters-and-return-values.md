---
title: 註釋函式參數和傳回值
ms.date: 10/15/2019
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Ouptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
- _Scanf_format_string_
- _Scanf_s_format_string_
- _Printf_format_string_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 16e7ffb30dc7ec4ae1b78647a0964b81932617ab
ms.sourcegitcommit: 174c992ecdc868ecbf7d3cee654bbc2855aeb67d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2019
ms.locfileid: "74879265"
---
# <a name="annotating-function-parameters-and-return-values"></a>註釋函式參數和傳回值
本文描述簡單函式參數（純量）和結構和類別的指標，以及大多數類型的緩衝區之注釋的一般用法。  本文也會說明批註的常見使用模式。 如需與函式相關的其他批註，請參閱批註函式[行為](../code-quality/annotating-function-behavior.md)。

## <a name="pointer-parameters"></a>指標參數
針對下表中的批註，當標注指標參數時，分析器會在指標為 null 時報告錯誤。  這適用于指標和指向的任何資料項目。

**注釋和描述**

- `_In_`

     標注輸入參數，其為純量、結構、結構的指標，以及 like。  明確可能用於簡單純量。  參數在預先狀態中必須是有效的，而且不會修改。

- `_Out_`

     標注輸出參數，其為純量、結構、結構的指標，以及 like。  請勿將此套用到無法傳回值的物件，例如，以傳值方式傳遞的純量。  參數在預先狀態中不一定是有效的，但在後置狀態中必須是有效的。

- `_Inout_`

     標注將由函式變更的參數。  它必須在前置狀態和後置狀態中都是有效的，但假設在呼叫前後有不同的值。 必須套用至可修改的值。

- `_In_z_`

     以 null 結束的字串指標，用來做為輸入。  此字串在前置狀態中必須是有效的。  慣用的 `PSTR`的變體已經有正確的批註。

- `_Inout_z_`

     將修改之以 null 結束之字元陣列的指標。  它在呼叫之前和之後都必須是有效的，但值會假設為已變更。  可以移動 null 結束字元，但只能存取最多到原始 null 結束字元的元素。

- `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     陣列的指標，由函數讀取。  陣列的大小 `s` 元素，全部都必須是有效的。

     `_bytes_` variant 會提供以位元組為單位的大小，而不是元素。 只有當大小無法以元素表示時，才使用此專案。  例如，只有在使用 `wchar_t` 的類似函式時，`char` 字串才會使用 `_bytes_` variant。

- `_In_reads_z_(s)`

     陣列的指標，其以 null 結束且具有已知的大小。 直到 null 結束字元為止的元素（如果沒有 null 結束字元，則為 `s`）必須在前置狀態中有效。  如果大小是以位元組為單位，則會依元素大小來調整 `s`。

- `_In_reads_or_z_(s)`

     陣列的指標，其以 null 結束或具有已知大小，或兩者皆為。 直到 null 結束字元為止的元素（如果沒有 null 結束字元，則為 `s`）必須在前置狀態中有效。  如果大小是以位元組為單位，則會依元素大小來調整 `s`。  （用於 `strn` 系列）。

- `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     函式將寫入的 `s` 元素陣列的指標（resp 位元組）。  陣列元素不一定要在前置狀態中有效，而且在後置狀態中有效的元素數目也不會指定。  如果參數類型上有批註，則會在後置狀態下套用。 例如，試想下列程式碼。

     ```cpp
     typedef _Null_terminated_ wchar_t *PWSTR;
     void MyStringCopy(_Out_writes_(size) PWSTR p1, _In_ size_t size, _In_ PWSTR p2);
     ```

     在此範例中，呼叫端會為 `p1`提供 `size` 元素的緩衝區。  `MyStringCopy` 使其中部分元素有效。 更重要的是，`PWSTR` 上的 `_Null_terminated_` 注釋表示 `p1` 在後置狀態中是以 null 終止。  如此一來，有效元素的數目仍然定義良好，但不需要特定的元素計數。

     `_bytes_` variant 會提供以位元組為單位的大小，而不是元素。 只有當大小無法以元素表示時，才使用此專案。  例如，只有在使用 `wchar_t` 的類似函式時，`char` 字串才會使用 `_bytes_` variant。

- `_Out_writes_z_(s)`

     `s` 元素陣列的指標。  元素在預先狀態中不一定是有效的。  在後置狀態中，已完成 null 結束字元的元素（必須存在）必須是有效的。  如果大小是以位元組為單位，則會依元素大小來調整 `s`。

- `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     陣列的指標，在函式中讀取和寫入。  其大小 `s` 元素，且在前置狀態和後置狀態中有效。

     `_bytes_` variant 會提供以位元組為單位的大小，而不是元素。 只有當大小無法以元素表示時，才使用此專案。  例如，只有在使用 `wchar_t` 的類似函式時，`char` 字串才會使用 `_bytes_` variant。

- `_Inout_updates_z_(s)`

     陣列的指標，其以 null 結束且具有已知的大小。 完成 null 結束字元的元素（必須存在）必須是前置狀態和後置狀態中的有效專案。  後置狀態中的值會假設為與前置狀態中的值不同。這包括 null 結束字元的位置。 如果大小是以位元組為單位，則會依元素大小來調整 `s`。

- `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     `s` 元素陣列的指標。  元素在預先狀態中不一定是有效的。  在後置狀態中，最多 `c`個元素的元素必須是有效的。  如果大小是以位元組為單位，而不是元素數目，則可以使用 `_bytes_` 變異。
     
     例如：

     ```cpp
     void *memcpy(_Out_writes_bytes_all_(s) char *p1, _In_reads_bytes_(s) char *p2, _In_ int s); 
     void *wordcpy(_Out_writes_all_(s) DWORD *p1, _In_reads_(s) DWORD *p2, _In_ int s);
     ```

- `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     陣列的指標，這是函式的讀取和寫入。  它的大小 `s` 元素，全都必須在前置狀態中有效，且 `c` 元素在後置狀態中必須是有效的。

     `_bytes_` variant 會提供以位元組為單位的大小，而不是元素。 只有當大小無法以元素表示時，才使用此專案。  例如，只有在使用 `wchar_t` 的類似函式時，`char` 字串才會使用 `_bytes_` variant。

- `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     陣列的指標，這是由大小 `s` 元素的函式讀取和寫入。 定義為相當於：

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     換句話說，在前置狀態下，`s` 緩衝區中的每個專案，都是在前置狀態和後置狀態中有效的。

     `_bytes_` variant 會提供以位元組為單位的大小，而不是元素。 只有當大小無法以元素表示時，才使用此專案。  例如，只有在使用 `wchar_t` 的類似函式時，`char` 字串才會使用 `_bytes_` variant。

- `_In_reads_to_ptr_(p)`

     陣列的指標，其中 `p - _Curr_` （也就是 `p` 減 `_Curr_`）是有效的運算式。  `p` 之前的元素必須在前置狀態中有效。

    例如：
    ```cpp
    int ReadAllElements(_In_reads_to_ptr_(EndOfArray) const int *Array, const int *EndOfArray);
    ```

- `_In_reads_to_ptr_z_(p)`

     Null 結束陣列的指標，其運算式 `p - _Curr_` （也就是 `p` 減 `_Curr_`）是有效的運算式。  `p` 之前的元素必須在前置狀態中有效。

- `_Out_writes_to_ptr_(p)`

     陣列的指標，其中 `p - _Curr_` （也就是 `p` 減 `_Curr_`）是有效的運算式。  `p` 之前的元素不一定要在預先狀態中有效，而且在後置狀態中必須是有效的。

- `_Out_writes_to_ptr_z_(p)`

     以 null 結束之陣列的指標，其 `p - _Curr_` （也就是 `p` 減 `_Curr_`）是有效的運算式。  `p` 之前的元素不一定要在預先狀態中有效，而且在後置狀態中必須是有效的。

## <a name="optional-pointer-parameters"></a>選擇性指標參數

當指標參數注釋包含 `_opt_`時，表示參數可能是 null。 否則，批註會與不包含 `_opt_`的版本執行相同的工作。 以下是指標參數注釋的 `_opt_` 變體清單：

||||
|-|-|-|
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|

## <a name="output-pointer-parameters"></a>輸出指標參數
輸出指標參數需要特殊的標記法，以區分參數上的 null 性質和指向的位置。

**注釋和描述**

- `_Outptr_`

   參數不可以是 null，而且在後置狀態中，指向的位置不能是 null，而且必須有效。

- `_Outptr_opt_`

   參數可以是 null，但在後置狀態中，指向的位置不能是 null，而且必須有效。

- `_Outptr_result_maybenull_`

   參數不可以是 null，而且在後置狀態中，指向的位置可以是 null。

- `_Outptr_opt_result_maybenull_`

   參數可以是 null，而在後置狀態中，指向的位置可以是 null。

  在下表中，其他子字串會插入批註名稱中，以進一步限定注釋的意義。  各種子字串為 `_z`、`_COM_`、`_buffer_`、`_bytebuffer_`和 `_to_`。

> [!IMPORTANT]
> 如果您要標注的介面是 COM，請使用這些批註的 COM 形式。 請勿將 COM 注釋與任何其他類型介面搭配使用。

**注釋和描述**

- `_Outptr_result_z_`

   `_Outptr_opt_result_z_`

   `_Outptr_result_maybenull_z_`

   `_Ouptr_opt_result_maybenull_z_`

   傳回的指標具有 `_Null_terminated_` 注釋。

- `_COM_Outptr_`

   `_COM_Outptr_opt_`

   `_COM_Outptr_result_maybenull_`

   `_COM_Outptr_opt_result_maybenull_`

   傳回的指標具有 COM 語義，因此會攜帶傳回的指標為 null 的 `_On_failure_` 後置條件。

- `_Outptr_result_buffer_(s)`

   `_Outptr_result_bytebuffer_(s)`

   `_Outptr_opt_result_buffer_(s)`

   `_Outptr_opt_result_bytebuffer_(s)`

   傳回的指標會指向大小 `s` 元素或位元組的有效緩衝區。

- `_Outptr_result_buffer_to_(s, c)`

   `_Outptr_result_bytebuffer_to_(s, c)`

   `_Outptr_opt_result_buffer_to_(s,c)`

   `_Outptr_opt_result_bytebuffer_to_(s,c)`

   傳回的指標指向大小為 `s` 元素或位元組的緩衝區，其中第一個 `c` 是有效的。

  某些介面慣例假設輸出參數會在失敗時 nullified。  除了明確的 COM 程式碼以外，下表中的表單是慣用的。  針對 COM 程式碼，請使用上一節中所列的對應 COM 表單。

  **注釋和描述**

- `_Result_nullonfailure_`

   修改其他批註。 如果函數失敗，結果會設定為 null。

- `_Result_zeroonfailure_`

   修改其他批註。 如果函數失敗，結果會設定為零。

- `_Outptr_result_nullonfailure_`

   如果函式成功，傳回的指標會指向有效的緩衝區; 如果函式失敗，則為 null。 此注釋適用于非選擇性的參數。

- `_Outptr_opt_result_nullonfailure_`

   如果函式成功，傳回的指標會指向有效的緩衝區; 如果函式失敗，則為 null。 此注釋適用于選擇性參數。

- `_Outref_result_nullonfailure_`

   如果函式成功，傳回的指標會指向有效的緩衝區; 如果函式失敗，則為 null。 此注釋適用于參考參數。

## <a name="output-reference-parameters"></a>輸出參考參數

參考參數的常見用法是用於輸出參數。  對於簡單的輸出參考參數，例如 `int&`，`_Out_` 提供正確的語法。  不過，當輸出值為指標（例如 `int *&`）時，`_Outptr_ int **` 的相等指標注釋就不會提供正確的語義。  若要以簡明的表示指標類型的輸出參考參數的語法，請使用下列複合批註：

**注釋和描述**

- `_Outref_`

     結果在後置狀態中必須是有效的，而且不能是 null。

- `_Outref_result_maybenull_`

     結果在後置狀態中必須是有效的，但在後置狀態中可能是 null。

- `_Outref_result_buffer_(s)`

     結果在後置狀態中必須是有效的，而且不能是 null。 指向大小 `s` 元素的有效緩衝區。

- `_Outref_result_bytebuffer_(s)`

     結果在後置狀態中必須是有效的，而且不能是 null。 指向大小為 `s` 位元組的有效緩衝區。

- `_Outref_result_buffer_to_(s, c)`

     結果在後置狀態中必須是有效的，而且不能是 null。 指向 `s` 元素的緩衝區，其中第一個 `c` 是有效的。

- `_Outref_result_bytebuffer_to_(s, c)`

     結果在後置狀態中必須是有效的，而且不能是 null。 指向第一個 `c` 有效 `s` 位元組的緩衝區。

- `_Outref_result_buffer_all_(s)`

     結果在後置狀態中必須是有效的，而且不能是 null。 指向有效的大小緩衝區，`s` 有效的元素。

- `_Outref_result_bytebuffer_all_(s)`

     結果在後置狀態中必須是有效的，而且不能是 null。 指向有效元素 `s` 位元組的有效緩衝區。

- `_Outref_result_buffer_maybenull_(s)`

     結果在後置狀態中必須是有效的，但在後置狀態中可能是 null。 指向大小 `s` 元素的有效緩衝區。

- `_Outref_result_bytebuffer_maybenull_(s)`

     結果在後置狀態中必須是有效的，但在後置狀態中可能是 null。 指向大小為 `s` 位元組的有效緩衝區。

- `_Outref_result_buffer_to_maybenull_(s, c)`

     結果在後置狀態中必須是有效的，但在後置狀態中可能是 null。 指向 `s` 元素的緩衝區，其中第一個 `c` 是有效的。

- `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     結果在後置狀態中必須是有效的，但在 post 狀態中可能會是 null。 指向第一個 `c` 有效 `s` 位元組的緩衝區。

- `_Outref_result_buffer_all_maybenull_(s)`

     結果在後置狀態中必須是有效的，但在 post 狀態中可能會是 null。 指向有效的大小緩衝區，`s` 有效的元素。

- `_Outref_result_bytebuffer_all_maybenull_(s)`

     結果在後置狀態中必須是有效的，但在 post 狀態中可能會是 null。 指向有效元素 `s` 位元組的有效緩衝區。

## <a name="return-values"></a>傳回值

函式的傳回值類似于 `_Out_` 參數，但在不同的取消參考層級，而且您不需要考慮結果指標的概念。  針對下列注釋，傳回值是批註物件（純量、結構的指標或緩衝區的指標）。 這些批註與對應的 `_Out_` 注釋具有相同的語義。

|||
|-|-|
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|

## <a name="format-string-parameters"></a>格式字串參數

- `_Printf_format_string_` 表示參數是用於 `printf` 運算式中的格式字串。

     **範例**

    ```cpp
    int MyPrintF(_Printf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwprintf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_format_string_` 表示參數是用於 `scanf` 運算式中的格式字串。

     **範例**

    ```cpp
    int MyScanF(_Scanf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_s_format_string_` 表示參數是用於 `scanf_s` 運算式中的格式字串。

     **範例**

    ```cpp
    int MyScanF_s(_Scanf_s_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf_s(format, args);
           va_end(args);
           return ret;
    }
    ```

## <a name="other-common-annotations"></a>其他常見注釋

**注釋和描述**

- `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     參數、欄位或結果會在範圍內（含），從 `low` 到 `hi`。  相當於套用至標注物件的 `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)`，以及適當的前置狀態或後置狀態條件。

    > [!IMPORTANT]
    > 雖然名稱包含「in」和「out」，但 `_In_` 和 `_Out_` 的語義**並不適用于**這些注釋。

- `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     標注的值完全是 `expr`。  相當於套用至標注物件的 `_Satisfies_(_Curr_ == expr)`，以及適當的前置狀態或後置狀態條件。

- `_Struct_size_bytes_(size)`

     適用于結構或類別宣告。  表示該類型的有效物件可能大於宣告的類型，但 `size`所提供的位元組數目。  例如：

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     `MyStruct *` 類型的參數 `pM` 的緩衝區大小（以位元組為單位），則會被視為：

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="related-resources"></a>相關資源

[程式碼分析小組 Blog](https://blogs.msdn.microsoft.com/codeanalysis/)

## <a name="see-also"></a>請參閱

- [使用 SAL 註釋減少 C/C++ 程式碼的缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [了解 SAL](../code-quality/understanding-sal.md)
- [註釋函式行為](../code-quality/annotating-function-behavior.md)
- [註釋結構和類別](../code-quality/annotating-structs-and-classes.md)
- [註釋鎖定行為](../code-quality/annotating-locking-behavior.md)
- [指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [內建函式](../code-quality/intrinsic-functions.md)
- [最佳做法和範例](../code-quality/best-practices-and-examples-sal.md)
