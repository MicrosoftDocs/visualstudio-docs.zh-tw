---
title: 標注函式參數和傳回值 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 71854388f3fb1c5eaea7d40ed2757af9cecacf1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543802"
---
# <a name="annotating-function-parameters-and-return-values"></a>註釋函式參數和傳回值
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本文描述簡單的函式參數（純量）和結構和類別的指標，以及大部分的緩衝區類型的附注一般用法。  本文也會顯示批註的常見使用模式。 如需與函式相關的其他批註，請參閱批註函式 [行為](../code-quality/annotating-function-behavior.md)  
  
## <a name="pointer-parameters"></a>指標參數  
 針對下表中的注釋，當指標參數正在標注時，如果指標為 null，分析器會回報錯誤。  這適用于指標和指向的任何資料項目。  
  
 **批註和描述**  
  
- `_In_`  
  
     標注具有純量、結構、結構指標和 like 的輸入參數。  明確地可用於簡單的純量。  參數必須在前置狀態中有效，且不會被修改。  
  
- `_Out_`  
  
     標注具有純量、結構、結構指標和 like 的輸出參數。  請勿將此套用至無法傳回值的物件，例如，以傳值方式傳遞的純量。  參數在前置狀態中不一定是有效的，但在之後的狀態中必須是有效的。  
  
- `_Inout_`  
  
     標注函式將變更的參數。  它必須在前置狀態和後置狀態中都是有效的，但假設在呼叫前後有不同的值。 必須套用至可修改的值。  
  
- `_In_z_`  
  
     以 null 結束的字串指標，用來做為輸入。  字串在前置狀態中必須是有效的。  慣用的變體 `PSTR` 已具有正確的注釋。  
  
- `_Inout_z_`  
  
     將修改之以 null 結束的字元陣列指標。  它在呼叫前後必須是有效的，但值會假設為已變更。  可能會移動 null 結束字元，但只能存取最多可存取原始 null 結束字元的元素。  
  
- `_In_reads_(s)`  
  
     `_In_reads_bytes_(s)`  
  
     陣列的指標，此函式會讀取該陣列。  陣列是大小的 `s` 元素，全部都必須是有效的。  
  
     `_bytes_`Variant 提供大小（以位元組為單位），而非元素。 只有在無法以元素表示時，才使用此值。  例如， `char` 字串只有在使用的類似函式時，才會使用 `_bytes_` variant `wchar_t` 。  
  
- `_In_reads_z_(s)`  
  
     陣列的指標，該陣列是以 null 終止，且具有已知的大小。 最多為 null 結束字元的元素（ `s` 如果沒有 null 結束字元）必須在前置狀態中有效。  如果大小是以位元組為單位，則 `s` 依元素大小進行調整。  
  
- `_In_reads_or_z_(s)`  
  
     陣列的指標，該陣列是以 null 終止或具有已知大小，或兩者都有。 最多為 null 結束字元的元素（ `s` 如果沒有 null 結束字元）必須在前置狀態中有效。  如果大小是以位元組為單位，則 `s` 依元素大小進行調整。  用於系列的 (`strn` 。 )   
  
- `_Out_writes_(s)`  
  
     `_Out_writes_bytes_(s)`  
  
     元素陣列的指標， `s` (resp 將由函式寫入) 。  陣列元素不一定要在前置狀態中有效，而且在後置狀態中有效的元素數目也不會指定。  如果參數類型上有注釋，則會套用至後續狀態。 例如，試想下列程式碼。  
  
     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`  
  
     在此範例中，呼叫端會提供的 `size` 元素緩衝區 `p1` 。  `MyStringCopy` 使其中一些元素有效。 更重要的 `_Null_terminated_` 是，上的注釋 `PWSTR` 表示 `p1` 在 post 狀態中是以 null 結束。  如此一來，仍然妥善定義有效元素的數目，但不需要特定的元素計數。  
  
     `_bytes_`Variant 提供大小（以位元組為單位），而非元素。 只有在無法以元素表示時，才使用此值。  例如， `char` 字串只有在使用的類似函式時，才會使用 `_bytes_` variant `wchar_t` 。  
  
- `_Out_writes_z_(s)`  
  
     元素陣列的指標 `s` 。  這些元素不一定要在前置狀態中有效。  在後置狀態中，透過 null 結束字元的元素（必須存在）必須是有效的。  如果大小是以位元組為單位，則 `s` 依元素大小進行調整。  
  
- `_Inout_updates_(s)`  
  
     `_Inout_updates_bytes_(s)`  
  
     陣列的指標，此陣列會在函式中讀取和寫入。  它是大小的 `s` 元素，而且在前置狀態和後置狀態中都是有效的。  
  
     `_bytes_`Variant 提供大小（以位元組為單位），而非元素。 只有在無法以元素表示時，才使用此值。  例如， `char` 字串只有在使用的類似函式時，才會使用 `_bytes_` variant `wchar_t` 。  
  
- `_Inout_updates_z_(s)`  
  
     陣列的指標，該陣列是以 null 終止，且具有已知的大小。 透過 null 結束字元（必須存在）上的元素必須在前置狀態和後置狀態中都是有效的。  Post 狀態中的值會假設與前置狀態中的值不同。這包括 null 結束字元的位置。 如果大小是以位元組為單位，則 `s` 依元素大小進行調整。  
  
- `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     元素陣列的指標 `s` 。  這些元素不一定要在前置狀態中有效。  在後置狀態中，最多專案的元素 `c` 必須是有效的。  如果大小是以位元組為單位，請調整規模， `s` 並 `c` 依元素大小或使用 `_bytes_` variant，其定義為：  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     換句話說，存在於緩衝區內的每個專案在前置狀態中 `s` 都是有效的（在後置狀態下）。  例如：  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
- `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     陣列的指標，函式會讀取和寫入陣列。  這是大小的 `s` 元素，這些元素全都必須在前置狀態下有效，且 `c` 元素必須在後置狀態中有效。  
  
     `_bytes_`Variant 提供大小（以位元組為單位），而非元素。 只有在無法以元素表示時，才使用此值。  例如， `char` 字串只有在使用的類似函式時，才會使用 `_bytes_` variant `wchar_t` 。  
  
- `_Inout_updates_z_(s)`  
  
     陣列的指標，該陣列是以 null 終止，且具有已知的大小。 透過 null 結束字元（必須存在）上的元素必須在前置狀態和後置狀態中都是有效的。  Post 狀態中的值會假設與前置狀態中的值不同。這包括 null 結束字元的位置。 如果大小是以位元組為單位，則 `s` 依元素大小進行調整。  
  
- `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     元素陣列的指標 `s` 。  這些元素不一定要在前置狀態中有效。  在後置狀態中，最多專案的元素 `c` 必須是有效的。  如果大小是以位元組為單位，請調整規模， `s` 並 `c` 依元素大小或使用 `_bytes_` variant，其定義為：  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     換句話說，存在於緩衝區內的每個專案在前置狀態中 `s` 都是有效的（在後置狀態下）。  例如：  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
- `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     陣列的指標，函式會讀取和寫入陣列。  這是大小的 `s` 元素，這些元素全都必須在前置狀態下有效，且 `c` 元素必須在後置狀態中有效。  
  
     `_bytes_`Variant 提供大小（以位元組為單位），而非元素。 只有在無法以元素表示時，才使用此值。  例如， `char` 字串只有在使用的類似函式時，才會使用 `_bytes_` variant `wchar_t` 。  
  
- `_Inout_updates_all_(s)`  
  
     `_Inout_updates_bytes_all_(s)`  
  
     陣列的指標，它是由大小元素的函式讀取和寫入 `s` 。 定義為相當於：  
  
     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`  
  
     換句話說，存在於緩衝區內的每個專案在前置狀態中 `s` 都是有效的，而且在前置狀態和後置狀態中都是有效的。  
  
     `_bytes_`Variant 提供大小（以位元組為單位），而非元素。 只有在無法以元素表示時，才使用此值。  例如， `char` 字串只有在使用的類似函式時，才會使用 `_bytes_` variant `wchar_t` 。  
  
- `_In_reads_to_ptr_(p)`  
  
     陣列的指標，該陣列的運算式 `p` `_Curr_` (為， `p` 減去 `_Curr_`) 是由適當的語言標準定義。  之前的元素 `p` 必須在前置狀態中有效。  
  
- `_In_reads_to_ptr_z_(p)`  
  
     以 null 終止陣列的指標，其運算式 `p` `_Curr_` (也就是， `p` 減去 `_Curr_`) 是由適當的語言標準定義。  之前的元素 `p` 必須在前置狀態中有效。  
  
- `_Out_writes_to_ptr_(p)`  
  
     陣列的指標，該陣列的運算式 `p` `_Curr_` (為， `p` 減去 `_Curr_`) 是由適當的語言標準定義。  之前的專案 `p` 不一定要在前置狀態中有效，且必須在後置狀態中有效。  
  
- `_Out_writes_to_ptr_z_(p)`  
  
     以 null 終止陣列的指標，其運算式 `p` `_Curr_` (也就是， `p` 減去 `_Curr_`) 是由適當的語言標準定義。  之前的專案 `p` 不一定要在前置狀態中有效，且必須在後置狀態中有效。  
  
## <a name="optional-pointer-parameters"></a>選擇性的指標參數  
 當指標參數注釋包含時 `_opt_` ，它會指出參數可以是 null。 否則，批註會執行與不包含的版本相同的 `_opt_` 。 以下是 `_opt_` 指標參數注釋的 variant 清單：  
  
`_In_opt_`, `_Out_opt_`, `_Inout_opt_`, `_In_opt_z_`, `_Inout_opt_z_`, `_In_reads_opt_`, `_In_reads_bytes_opt_`, `_In_reads_opt_z_`|`_Out_writes_opt_`, `_Out_writes_opt_z_`, `_Inout_updates_opt_`, `_Inout_updates_bytes_opt_`, `_Inout_updates_opt_z_`, `_Out_writes_to_opt_`, `_Out_writes_bytes_to_opt_`, `_Out_writes_all_opt_`, `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`, `_Inout_updates_bytes_to_opt_`, `_Inout_updates_all_opt_`, `_Inout_updates_bytes_all_opt_`, `_In_reads_to_ptr_opt_`, `_In_reads_to_ptr_opt_z_`, `_Out_writes_to_ptr_opt_`, `_Out_writes_to_ptr_opt_z_`|  
  
## <a name="output-pointer-parameters"></a>輸出指標參數  
 Output 指標參數需要特殊標記法，以區分參數上的 null 性質和指向的位置。  
  
 **批註和描述**  
  
- `_Outptr_`  
  
   參數不可以是 null，而且在之後的狀態下，指向位置不可以是 null，而且必須是有效的。  
  
- `_Outptr_opt_`  
  
   參數可以是 null，但在之後的狀態下，指向位置不可以是 null，而且必須是有效的。  
  
- `_Outptr_result_maybenull_`  
  
   參數不可以是 null，而且在之後的狀態下，指向位置可以是 null。  
  
- `_Outptr_opt_result_maybenull_`  
  
   參數可以是 null，而且在之後的狀態下，指向位置可以是 null。  
  
  在下表中，會在批註名稱中插入額外的子字串，以進一步限定批註的意義。  不同的子字串包括 `_z` 、、 `_COM_` `_buffer_` 、 `_bytebuffer_` 和 `_to_` 。  
  
> [!IMPORTANT]
> 如果您要標注的介面是 COM，請使用這些批註的 COM 形式。 請勿搭配任何其他類型介面使用 COM 注釋。  
  
 **批註和描述**  
  
- `_Outptr_result_z_`  
  
   `_Outptr_opt_result_z_`  
  
   `_Outptr_result_maybenull_z_`  
  
   `_Ouptr_opt_result_maybenull_z_`  
  
   傳回的指標有 `_Null_terminated_` 批註。  
  
- `_COM_Outptr_`  
  
   `_COM_Outptr_opt_`  
  
   `_COM_Outptr_result_maybenull_`  
  
   `_COM_Outptr_opt_result_maybenull_`  
  
   傳回的指標具有 COM 語義，因此 `_On_failure_` 會產生傳回的指標為 null 的後置條件。  
  
- `_Outptr_result_buffer_(s)`  
  
   `_Outptr_result_bytebuffer_(s)`  
  
   `_Outptr_opt_result_buffer_(s)`  
  
   `_Outptr_opt_result_bytebuffer_(s)`  
  
   傳回的指標指向大小 `s` 元素或位元組的有效緩衝區。  
  
- `_Outptr_result_buffer_to_(s, c)`  
  
   `_Outptr_result_bytebuffer_to_(s, c)`  
  
   `_Outptr_opt_result_buffer_to_(s,c)`  
  
   `_Outptr_opt_result_bytebuffer_to_(s,c)`  
  
   傳回的指標指向大小 `s` 元素或位元組的緩衝區，其中第一個 `c` 是有效的。  
  
  某些介面慣例假設輸出參數會在失敗時 nullified。  除了明確的 COM 程式碼以外，下表中的表單是慣用的。  針對 COM 程式碼，請使用上一節中所列的對應 COM 表單。  
  
  **批註和描述**  
  
- `_Result_nullonfailure_`  
  
   修改其他注釋。 如果函式失敗，結果會設為 null。  
  
- `_Result_zeroonfailure_`  
  
   修改其他注釋。 如果函式失敗，結果會設為零。  
  
- `_Outptr_result_nullonfailure_`  
  
   如果函式成功，傳回的指標會指向有效的緩衝區，如果函式失敗，則為 null。 此注釋適用于非選擇性的參數。  
  
- `_Outptr_opt_result_nullonfailure_`  
  
   如果函式成功，傳回的指標會指向有效的緩衝區，如果函式失敗，則為 null。 此注釋適用于選擇性參數。  
  
- `_Outref_result_nullonfailure_`  
  
   如果函式成功，傳回的指標會指向有效的緩衝區，如果函式失敗，則為 null。 此注釋適用于參考參數。  
  
## <a name="output-reference-parameters"></a>輸出參考參數  
 參考參數的常見用法是用於輸出參數。  針對簡單的輸出參考參數（例如） `int&` ， `_Out_` 提供正確的語法。  不過，當輸出值為指標時（例如）， `int *&` 對等的指標注釋（例如） `_Outptr_ int **` 不會提供正確的語法。  若要簡潔表達指標類型之輸出參考參數的語法，請使用下列複合批註：  
  
 **批註和描述**  
  
- `_Outref_`  
  
     結果在 post 狀態中必須是有效的，而且不可以是 null。  
  
- `_Outref_result_maybenull_`  
  
     結果必須是有效的 post 狀態，但在 post 狀態中可能是 null。  
  
- `_Outref_result_buffer_(s)`  
  
     結果在 post 狀態中必須是有效的，而且不可以是 null。 指向大小元素的有效緩衝區 `s` 。  
  
- `_Outref_result_bytebuffer_(s)`  
  
     結果在 post 狀態中必須是有效的，而且不可以是 null。 指向大小位元組的有效緩衝區 `s` 。  
  
- `_Outref_result_buffer_to_(s, c)`  
  
     結果在 post 狀態中必須是有效的，而且不可以是 null。 指向元素的緩衝區 `s` ，其中第一個 `c` 是有效的。  
  
- `_Outref_result_bytebuffer_to_(s, c)`  
  
     結果在 post 狀態中必須是有效的，而且不可以是 null。 指向 `s` 第一個有效的位元組緩衝區 `c` 。  
  
- `_Outref_result_buffer_all_(s)`  
  
     結果在 post 狀態中必須是有效的，而且不可以是 null。 指向大小有效元素的有效緩衝區 `s` 。  
  
- `_Outref_result_bytebuffer_all_(s)`  
  
     結果在 post 狀態中必須是有效的，而且不可以是 null。 指向有效元素的有效 `s` 位元組緩衝區。  
  
- `_Outref_result_buffer_maybenull_(s)`  
  
     結果必須是有效的 post 狀態，但在 post 狀態中可能是 null。 指向大小元素的有效緩衝區 `s` 。  
  
- `_Outref_result_bytebuffer_maybenull_(s)`  
  
     結果必須是有效的 post 狀態，但在 post 狀態中可能是 null。 指向大小位元組的有效緩衝區 `s` 。  
  
- `_Outref_result_buffer_to_maybenull_(s, c)`  
  
     結果必須是有效的 post 狀態，但在 post 狀態中可能是 null。 指向元素的緩衝區 `s` ，其中第一個 `c` 是有效的。  
  
- `_Outref_result_bytebuffer_to_maybenull_(s,c)`  
  
     結果在 post 狀態中必須是有效的，但在 post 狀態中可能是 null。 指向 `s` 第一個有效的位元組緩衝區 `c` 。  
  
- `_Outref_result_buffer_all_maybenull_(s)`  
  
     結果在 post 狀態中必須是有效的，但在 post 狀態中可能是 null。 指向大小有效元素的有效緩衝區 `s` 。  
  
- `_Outref_result_bytebuffer_all_maybenull_(s)`  
  
     結果在 post 狀態中必須是有效的，但在 post 狀態中可能是 null。 指向有效元素的有效 `s` 位元組緩衝區。  
  
## <a name="return-values"></a>傳回值  
 函式的傳回值類似于 `_Out_` 參數，但位於不同的取消參考層級，而且您不需要考慮結果指標的概念。  針對下列注釋，傳回值是批註物件（純量、結構的指標或緩衝區的指標）。 這些批註與對應的注釋具有相同的語法 `_Out_` 。  
  
`_Ret_z_`, `_Ret_writes_(s)`, `_Ret_writes_bytes_(s)`, `_Ret_writes_z_(s)`, `_Ret_writes_to_(s,c)`, `_Ret_writes_maybenull_(s)`, `_Ret_writes_to_maybenull_(s)`, `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`, `_Ret_maybenull_z_`, `_Ret_null_`, `_Ret_notnull_`, `_Ret_writes_bytes_to_`, `_Ret_writes_bytes_maybenull_`, `_Ret_writes_bytes_to_maybenull_`
  
## <a name="other-common-annotations"></a>其他常見注釋  
 **批註和描述**  
  
- `_In_range_(low, hi)`  
  
     `_Out_range_(low, hi)`  
  
     `_Ret_range_(low, hi)`  
  
     `_Deref_in_range_(low, hi)`  
  
     `_Deref_out_range_(low, hi)`  
  
     `_Deref_inout_range_(low, hi)`  
  
     `_Field_range_(low, hi)`  
  
     參數、欄位或結果位於 (內含) 的範圍 `low` `hi` 。  相當於套用 `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` 至標注的物件，以及適當的前置狀態或後置狀態的條件。  
  
    > [!IMPORTANT]
    > 雖然名稱包含 "in" 和 "out"，但是的語義 `_In_` 並不適 `_Out_` 用於**not**這些批註。  
  
- `_Pre_equal_to_(expr)`  
  
     `_Post_equal_to_(expr)`  
  
     批註值完全相符 `expr` 。  相當於套用 `_Satisfies_(_Curr_ == expr)` 至標注的物件，以及適當的前置狀態或後置狀態的條件。  
  
- `_Struct_size_bytes_(size)`  
  
     適用于結構或類別宣告。  指出該類型的有效物件可能大於宣告的型別，以及所提供的位元組數目 `size` 。  例如：  
  
     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`  
  
     然後，會將類型參數的緩衝區大小（以位元組為單位）視為 `pM` `MyStruct *` ：  
  
     `min(pM->nSize, sizeof(MyStruct))`  
  
## <a name="related-resources"></a>相關資源  
 [程式碼分析小組的 Blog](https://blogs.msdn.com/b/codeanalysis/)  
  
## <a name="see-also"></a>另請參閱  
 [使用 SAL 注釋減少 C/c + + 程式碼瑕疵](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [瞭解 SAL](../code-quality/understanding-sal.md)   
 [標注函式行為](../code-quality/annotating-function-behavior.md)   
 [標注結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [標注鎖定行為](../code-quality/annotating-locking-behavior.md)   
 [指定套用注釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [內建函式](../code-quality/intrinsic-functions.md)   
 [最佳做法和範例](../code-quality/best-practices-and-examples-sal.md)
