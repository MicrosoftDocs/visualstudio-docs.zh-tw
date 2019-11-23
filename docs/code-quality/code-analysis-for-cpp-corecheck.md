---
title: C++核心指導方針檢查程式參考
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 9a5fe14c1bcb2b375a104a928513134b1789d437
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745957"
---
# <a name="c-core-guidelines-checker-reference"></a>C++核心指導方針檢查程式參考

本節列出C++核心指導方針檢查程式警告。 如需程式碼分析的詳細資訊，請參閱[/analyze （程式碼分析）](/cpp/build/reference/analyze-code-analysis)和[快速入門：C++C/的程式碼分析](../code-quality/quick-start-code-analysis-for-c-cpp.md)。

> [!NOTE]
> 有些警告屬於一個以上的群組，而並非所有警告都有完整的參考主題。

## <a name="owner_pointer-group"></a>OWNER_POINTER 群組

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)傳回已設定範圍的物件，而不是堆積配置（如果它有移動函數）。 請參閱[ C++核心指導方針 R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。

[C26403 RESET_OR_DELETE_OWNER](C26403.md)重設或明確刪除擁有者\<T > 指標 '% variable% '。 請參閱[ C++核心指導方針 R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。

[C26404 DONT_DELETE_INVALID](C26404.md)請勿刪除可能處於無效狀態的擁有者\<T >。 請參閱[ C++核心指導方針 R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。

[C26405 DONT_ASSIGN_TO_VALID](C26405.md)請勿指派給擁有者\<T > 可能處於有效狀態。 請參閱[ C++核心指導方針 R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md)請勿將原始指標指派給擁有者\<T >。 請參閱[ C++核心指導方針 R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md)偏好設定範圍的物件，不會不必要地進行堆積配置。 請參閱[ C++核心指導方針 R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)。

[C26429 USE_NOTNull](C26429.md)符號 '% symbol% ' 從未測試過 null，可以標示為 not_null。 請參閱[ C++核心指導方針 F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。

[C26430 TEST_ON_ALL_PATHS](C26430.md)未在所有路徑上測試符號 '% symbol% ' 是否有 null。 請參閱[ C++核心指導方針 F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。

[C26431 DONT_TEST_NOTNull](C26431.md)運算式 '% expr% ' 的類型已經 gsl：： not_null。 請勿針對 null 進行測試。 請參閱[ C++核心指導方針 F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。

## <a name="raw_pointer-group"></a>RAW_POINTER 群組

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md)請勿將配置或函式呼叫的結果指派給擁有者\<T > 傳回值給原始指標;請改用 owner\<T >。 請參閱[ C++核心指導方針 I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw)。

[C26401 DONT_DELETE_NON_OWNER](c26401.md)請勿刪除不是擁有者\<T > 的原始指標。 請參閱[ C++核心指導方針 I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw)。

如果[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) ，  會傳回有範圍的物件，而不是堆積配置的（如果它有移動函數）。 請參閱[ C++核心指導方針 R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。

[C26408 NO_MALLOC_FREE](C26408.md)避免 malloc （）和 free （），建議使用 nothrow 版本的 new with delete。 請參閱[ C++核心指導方針 R. 10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree)。

[C26409 NO_NEW_DELETE](C26409.md)請避免明確呼叫 new 和 delete，請改用 std：： make_unique\<T >。 請參閱[ C++核心指導方針 R. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete)。

[C26429 USE_NOTNull](C26429.md)符號 '% symbol% ' 從未測試過 null，可以標示為 not_null。 請參閱[ C++核心指導方針 F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。

[C26430 TEST_ON_ALL_PATHS](C26430.md)未在所有路徑上測試符號 '% symbol% ' 是否有 null。 請參閱[ C++核心指導方針 F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。

[C26431 DONT_TEST_NOTNull](C26431.md)運算式 '% expr% ' 的類型已經 gsl：： not_null。 請勿針對 null 進行測試。 請參閱[ C++核心指導方針 F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。

[C26481 NO_POINTER_ARITHMETIC](C26481.md)不使用指標算術。 請改用 span。 請參閱[ C++核心指導方針範圍 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)。

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)。
運算式 '% expr% '：找不到指標衰減的陣列。 請參閱[ C++核心指導方針界限。 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)。

## <a name="unique_pointer-group"></a>UNIQUE_POINTER 群組

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md)參數 '% parameter% ' 是 `const` 唯一指標的參考，請改用 const T * 或 const T &。 請參閱[ C++核心指導方針 R. 32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam)。

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md)參數 '% parameter% ' 是唯一指標的參考，而且永遠不會重新指派或重設，請改用 T * 或 T &。 請參閱[ C++核心指導方針 R. 33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat)。

[C26414 RESET_LOCAL_SMART_PTR](C26414.md)移動、複製、重新指派或重設本機智能型指標 '% symbol% '。 請參閱[ C++核心指導方針 R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)。

[C26415 SMART_PTR_NOT_NEEDED](C26415.md)智慧型指標參數 '% symbol% ' 僅用於存取包含的指標。 請改用 T * 或 T &。 請參閱[ C++核心指導方針 R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam)。

## <a name="shared_pointer-group"></a>SHARED_POINTER 群組

[C26414 RESET_LOCAL_SMART_PTR](C26414.md)移動、複製、重新指派或重設本機智能型指標 '% symbol% '。 請參閱[ C++核心指導方針 R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)。

[C26415 SMART_PTR_NOT_NEEDED](C26415.md)智慧型指標參數 '% symbol% ' 僅用於存取包含的指標。 請改用 T * 或 T &。 請參閱[ C++核心指導方針 R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam)。

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md)共用指標參數 '% symbol% ' 是由右值參考所傳遞。 改為以傳值方式傳遞。 請參閱[ C++核心指導方針 R. 34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner)。

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md)共用指標參數 '% symbol% ' 是以傳址方式傳遞，而不是重設或重新指派。 請改用 T * 或 T &。 請參閱[ C++核心指導方針 R. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam)。

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md)未複製或移動共用指標參數 '% symbol% '。 請改用 T * 或 T &。 請參閱[ C++核心指導方針 R. 36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const)。

## <a name="declaration-group"></a>宣告群組

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md)全域初始化運算式會呼叫非 constexpr 函數 '% symbol% '。 請參閱[ C++核心指導方針 I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects)。

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md)全域初始化運算式存取外部物件 '% symbol% '。 請參閱[ C++核心指導方針 I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects)。

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md)使用自訂結構和終結來避免未命名的物件。 請參閱[ES：不要（嘗試）宣告沒有名稱的區域變數](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)。

## <a name="class-group"></a>類別群組

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md)如果您定義或刪除類型 '% symbol% ' 中的任何預設作業，請定義或刪除全部。 請參閱[ C++核心指導方針 C. 21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all)。

[C26433 OVERRIDE_EXPLICITLY](c26433.md)函式 '% 符號% ' 應該以 ' override ' 標記。 請參閱[C. 128：虛擬函式應該只指定其中一個虛擬、覆寫或最終](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final)。

[C26434 DONT_HIDE_METHODS](C26434.md)函數 '% symbol_1% ' 會隱藏非虛擬函數 '% symbol_2% '。 請參閱[ C++核心指導方針 c. 128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final)。

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md)函數 '% symbol% ' 應該只指定 ' virtual '、' override ' 或 ' final ' 其中之一。 請參閱[C. 128：虛擬函式應該只指定其中一個虛擬、覆寫或最終](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)。

[C26436 NEED_VIRTUAL_DTOR](C26436.md)具有虛擬函數的類型 '% 符號% ' 需要公用虛擬或受保護的非虛擬析構函式。 請參閱[ C++核心指導方針 C. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual)。

[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md)覆寫析構函式不應使用明確的 ' override ' 或 ' virtual ' 規範。 請參閱[C. 128：虛擬函式應該只指定其中一個虛擬、覆寫或最終](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)。

## <a name="type-group"></a>類型群組

[C26437 DONT_SLICE](C26437.md)不要配量。 請參閱[ C++核心指導方針 ES. 63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice)。

## <a name="style-group"></a>樣式群組

[C26438 NO_GOTO](C26438.md)避免 `goto`。 請參閱[ C++ Core 方針 ES. 76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto)。

## <a name="function-group"></a>函數群組

[C26439 SPECIAL_NOEXCEPT](C26439.md)這種函數可能不會擲回。 將它宣告 `noexcept`。 請參閱[ C++核心指導方針 f. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)。

[C26440 DECLARE_NOEXCEPT](C26440.md)函數 '% symbol% ' 可以 `noexcept`宣告。 請參閱[ C++核心指導方針 f. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)。

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md)函式會宣告為**noexcept** ，但會呼叫可能會擲回例外狀況的函式。
請參閱[ C++核心指導方針： F. 6：如果您的函式可能不會擲回，請將它宣告為 noexcept](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)。

## <a name="concurrency-group"></a>並行群組

[C26441 NO_UNNAMED_GUARDS](C26441.md)Guard 物件必須命名為。 請參閱[ C++核心指導方針 cp. 44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks)。

## <a name="const-group"></a>CONST 群組

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md)函數 '% function% ' 的參考引數 '% 引數% ' 可以標記為 `const`。 請參閱[ C++核心指導方針。 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref)。

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md)：函數 '% function% ' 的指標引數 '% argument% ' 可以標記為 `const`的指標。 請參閱[ C++核心指導方針。 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref)。

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md)'% Variable% ' 所指向的值只會指派一次，並將其標示為 `const`的指標。 請參閱[ C++核心指導方針。 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)。

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md)陣列 '% array% ' 的元素只會指派一次，`const`mark 元素。 請參閱[ C++核心指導方針。 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)。

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md)陣列 '% array% ' 的專案所指向的值只會指派一次，將元素標示為 `const`的指標。 請參閱[ C++核心指導方針。 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)。

[C26496 USE_CONST_FOR_VARIABLE](c26496.md)變數 '% variable% ' 只指派一次，將它標示為 `const`。 請參閱[ C++核心指導方針。 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)。

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md)如果需要編譯時間評估，可以將這個函數% function% 標記 `constexpr`。 請參閱[ C++核心指導方針 f. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr)。

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md)如果需要編譯時間評估，這個函式呼叫% function% 可以使用 `constexpr`。 請參閱[ C++核心指導方針。 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr)。

## <a name="type-group"></a>類型群組

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md)不要使用 `const_cast` 將 `const`轉型。 不需要 `const_cast`;此轉換不會移除常數性或變動性。 請參閱[ C++核心指導方針類型。 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast)。

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md)請勿使用 `static_cast` 向下轉換。 從多型類型轉換時，應該使用 dynamic_cast。 請參閱[ C++核心指導方針類型。 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast)。

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md)請勿使用 `reinterpret_cast`。 從 void * 轉換可以使用 `static_cast`。 請參閱[ C++核心指導方針類型 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)。

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md)不使用 `static_cast` 進行算術轉換。 使用大括弧初始化、gsl：： narrow_cast 或 gsl：： narow。 請參閱[ C++核心指導方針類型 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)。

[C26473 NO_IDENTITY_CAST](C26473.md)請勿在來源類型與目標型別相同的指標類型之間進行轉換。 請參閱[ C++核心指導方針類型 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)。

[C26474 NO_IMPLICIT_CAST](C26474.md)轉換可能是隱含的時，請勿在指標類型之間轉換。 請參閱[ C++核心指導方針類型 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)。

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md)請勿使用函數樣式 C 轉換。 請參閱[ C++核心指導方針 ES. 49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast)。

[C26490 NO_REINTERPRET_CAST](c26490.md)請勿使用 `reinterpret_cast`。 請參閱[ C++核心指導方針類型 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。

[C26491 NO_STATIC_DOWNCAST](c26490.md)請勿使用 `static_cast` 向下轉換。 請參閱[ C++核心指導方針類型。 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。

[C26492 NO_CONST_CAST](c26492.md)不用`const_cast`拋棄`const`。 請參閱[ C++核心指導方針類型。 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。

[C26493 NO_CSTYLE_CAST](c26493.md)不要使用 C 樣式轉換。 請參閱[ C++核心指導方針類型 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。

[C26494 VAR_USE_BEFORE_INIT](c26494.md)變數 '% variable% ' 未初始化。 一律初始化物件。 請參閱[ C++核心指導方針類型. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。

[C26495 誤判 MEMBER_UNINIT](c26495.md)變數 '% variable% ' 未初始化。 一律初始化成員變數。 請參閱[ C++核心指導方針類型 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。

## <a name="bounds-group"></a>界限群組

[C26446 USE_GSL_AT](c26446.md)偏好使用 `gsl::at()`，而不是取消核取的注標運算子。 請參閱[ C++核心指導方針：界限。4：不要使用不是界限檢查的標準程式庫函式和類型](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)。

[C26481 NO_POINTER_ARITHMETIC](C26481.md)。
不使用指標算術。 請改用 span。 請參閱[ C++核心指導方針範圍1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md)只有使用常數運算式的陣列索引。 請參閱[ C++核心指導方針界限2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md)值% value% 超出界限（0，% 界限%）（屬於變數 '% variable% '）。 僅使用陣列界限內的常數運算式來編制陣列的索引。 請參閱[ C++核心指導方針界限2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)運算式 '% expr% '：找不到指標衰減的陣列。 請參閱[ C++核心指導方針界限。3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>GSL 群組

[C26445 NO_SPAN_REF](c26445.md)`gsl::span` 或 `std::string_view` 的參考可能會指出存留期的問題。
請參閱[ C++核心指導方針 GSL。 view： Views](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md)偏好使用 `gsl::at()`，而不是取消核取的注標運算子。 請參閱[ C++核心指導方針：界限。4：不要使用不是界限檢查的標準程式庫函式和類型](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)。

[C26448 USE_GSL_FINALLY](c26448.md)如果想要執行最後的動作，請考慮使用 `gsl::finally`。 請參閱[ C++核心指導方針： GSL. util：公用程式](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities)。

當暫時失效時，從暫存建立的[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md)
`gsl::span` 或 `std::string_view` 將會無效。 請參閱[ C++核心指導方針： GSL： Views](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)。

## <a name="deprecated-warnings"></a>已淘汰的警告

下列警告存在於核心方針檢查程式的早期實驗性規則集內，但現在已被取代，可以放心忽略。 上述清單中的警告會取代警告。

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- 26422 VALID_OWNER_LEAVING_SCOPE
- 26423 ALLOCATION_NOT_ASSIGNED_TO_OWNER
- 26424 VALID_ALLOCATION_LEAVING_SCOPE
- 26425 ASSIGNING_TO_STATIC
- 26499 NO_LIFETIME_TRACKING

## <a name="see-also"></a>另請參閱
[使用C++核心指導方針檢查](using-the-cpp-core-guidelines-checkers.md)
