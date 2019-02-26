---
title: C + + Core Guidelines 檢查工具參考
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 6db375422e4a8d21d9b82cac82a07fed45e7d279
ms.sourcegitcommit: 1c8e07b98fc0a44b5ab90bcef77d9fac7b3eb452
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2019
ms.locfileid: "56796812"
---
# <a name="c-core-guidelines-checker-reference"></a>C + + Core Guidelines 檢查工具參考

本章節列出 c + + 核心指南檢查工具警告。 如需程式碼分析的資訊，請參閱 < [/analyze （程式碼分析）](/cpp/build/reference/analyze-code-analysis)和[快速入門：C/c + + 程式碼分析](../code-quality/quick-start-code-analysis-for-c-cpp.md)。

> [!NOTE]
> 某些警告屬於一個以上的群組，且並非所有的警告有完整的參考主題。

## <a name="ownerpointer-group"></a>OWNER_POINTER 群組

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)有移動建構函式會傳回範圍的物件，而不是堆積配置。 請參閱[c + + Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。

[C26403 RESET_OR_DELETE_OWNER](C26403.md)重設或明確刪除擁有者\<T > 指標 '%變數 %'。 請參閱[c + + Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。

[C26404 DONT_DELETE_INVALID](C26404.md)請勿刪除擁有者\<T > 可能處於無效狀態。 請參閱[c + + Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。

[C26405 DONT_ASSIGN_TO_VALID](C26405.md)沒有指派給擁有者\<T >，可能是處於有效狀態。 請參閱[c + + Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md)請勿將原始指標指派給擁有者\<T >。 請參閱[c + + Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md)建議使用有範圍的物件，不 nepřidělujte zbytečně haldu。 請參閱[c + + Core Guidelines R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)。

[C26429 USE_NOTNULL](C26429.md) null 值永遠不會測試符號 '%符號 %'、 not_null 標示。 請參閱[c + + Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。

[C26430 TEST_ON_ALL_PATHS](C26430.md)符號 '%符號 %' 並未經過測試，在所有路徑上的 null 值。 請參閱[c + + Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。

[C26431 DONT_TEST_NOTNULL](C26431.md)運算式 '%expr%' 的類型已經是 gsl:: not_null。 請勿測試其 null 值。 請參閱[c + + Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。

## <a name="rawpointer-group"></a>RAW_POINTER 群組

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md)請勿將配置或函式呼叫的結果指派具有擁有者\<T > 傳回給原始指標的值; 使用擁有者\<T > 改用。 請參閱[c + + Core Guidelines I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw)。

[C26401 DONT_DELETE_NON_OWNER](c26401.md)不會刪除不是擁有者的原始指標\<T >。 請參閱[c + + Core Guidelines I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw)。

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)  有移動建構函式會傳回範圍的物件，而不是堆積配置。 請參閱[c + + Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。

[C26408 NO_MALLOC_FREE](C26408.md)請避免 malloc 或 free （）、 使用 nothrow 版本的新增與刪除。 請參閱[c + + Core Guidelines R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree)。

[C26409 NO_NEW_DELETE](C26409.md)避免呼叫 new 及明確刪除，請使用 std\<T > 改用。 請參閱[c + + Core Guidelines R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete)。

[C26429 USE_NOTNULL](C26429.md) null 值永遠不會測試符號 '%符號 %'、 not_null 標示。 請參閱[c + + Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。

[C26430 TEST_ON_ALL_PATHS](C26430.md)符號 '%符號 %' 並未經過測試，在所有路徑上的 null 值。 請參閱[c + + Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。

[C26431 DONT_TEST_NOTNULL](C26431.md)運算式 '%expr%' 的類型已經是 gsl:: not_null。 請勿測試其 null 值。 請參閱[c + + Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。

[C26481 NO_POINTER_ARITHMETIC](C26481.md)不使用指標算術。 請改用 span。 請參閱[c + + 核心指南 Bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)。

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)。
'%Expr%' 的運算式：沒有指標衰減陣列。 請參閱[c + + 核心指南 Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)。

## <a name="uniquepointer-group"></a>UNIQUE_POINTER 群組

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md)參數 '%參數 %' 是參考`const`唯一指標，使用 const T * 或 const T& 改用。 請參閱[c + + Core Guidelines R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam)。

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md)參數 '%參數 %' 是唯一指標的參考，而且它永遠不會重新指派或重設，使用 T * 或 T& 改用。 請參閱[c + + Core Guidelines R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat)。

[C26414 RESET_LOCAL_SMART_PTR](C26414.md)移動、 複製、 重新指派，或重設本機智慧指標 '%符號 %'。 請參閱[c + + Core Guidelines R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)。

[C26415 SMART_PTR_NOT_NEEDED](C26415.md)智慧指標參數 '%符號 %' 只會用於存取自主的指標。 使用 T * 或 T& 改用。 請參閱[c + + Core Guidelines R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam)。

## <a name="sharedpointer-group"></a>SHARED_POINTER 群組

[C26414 RESET_LOCAL_SMART_PTR](C26414.md)移動、 複製、 重新指派，或重設本機智慧指標 '%符號 %'。 請參閱[c + + Core Guidelines R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)。

[C26415 SMART_PTR_NOT_NEEDED](C26415.md)智慧指標參數 '%符號 %' 只會用於存取自主的指標。 使用 T * 或 T& 改用。 請參閱[c + + Core Guidelines R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam)。

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md)共用指標參數 '%符號 %' 右值參考方式傳遞。 而是依值傳遞。 請參閱[c + + Core Guidelines R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner)。

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md)傳址方式傳遞並不會重設或重新指派共用指標參數 '%符號 %'。 使用 T * 或 T& 改用。 請參閱[c + + Core Guidelines R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam)。

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md)未複製或移動共用指標參數 '%符號 %'。 使用 T * 或 T& 改用。 請參閱[c + + Core Guidelines R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const)。

## <a name="declaration-group"></a>宣告群組

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md)全域初始設定式會呼叫非 constexpr 函式 '%符號 %'。 請參閱[c + + Core Guidelines I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects)。

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md)全域初始設定式會存取外部物件 '%符號 %'。 請參閱[c + + Core Guidelines I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects)。

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md)避免未命名的物件具有自訂建構和解構。 請參閱[ES.84:請勿 （嘗試） 宣告區域變數但沒有名稱](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)。

## <a name="class-group"></a>類別群組

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md)如果您定義或刪除任何預設作業類型 '%符號 %' 中的，定義或刪除它們全部。 請參閱[c + + Core Guidelines C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all)。

[C26433 OVERRIDE_EXPLICITLY](c26433.md)應該與 'override' 標記的函式 '%符號 %'。 請參閱[C.128:虛擬函式應指定剛好一個虛擬的覆寫，或最後一個](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final)。

[C26434 DONT_HIDE_METHODS](C26434.md)函式 '%symbol_1%' 會隱藏非虛擬函式 '%symbol_2%'。 請參閱[c + + Core Guidelines C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final)。

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md)函式 '%符號 %' 應指定剛好一個 'virtual'、 'override' 或 'final'。 請參閱[C.128:虛擬函式應指定剛好一個虛擬的覆寫，或最後一個](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)。


[C26436 NEED_VIRTUAL_DTOR](C26436.md)具有虛擬函式的 ' %符號 %' 的類型必須是公用虛擬或受保護非虛擬解構函式。 請參閱[c + + Core Guidelines C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual)。


[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md)覆寫解構函式不應使用明確的 'override' virtual' 的規範。 請參閱[C.128:虛擬函式應指定剛好一個虛擬的覆寫，或最後一個](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)。


## <a name="type-group"></a>型別群組

[C26437 DONT_SLICE](C26437.md)不配量。 請參閱[c + + Core Guidelines ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice)。

## <a name="style-group"></a>樣式 群組中

[C26438 NO_GOTO](C26438.md)避免`goto`。 請參閱[c + + Core Guidelines EX.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto)。

## <a name="function-group"></a>函式群組

[C26439 SPECIAL_NOEXCEPT](C26439.md)這種函式可能不會擲回。 將它宣告`noexcept`。 請參閱[c + + Core Guidelines F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)。

[C26440 DECLARE_NOEXCEPT](C26440.md)可以宣告為函式 '%符號 %' `noexcept`。 請參閱[c + + Core Guidelines F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)。

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md)函式宣告**noexcept**但 calls 函式可能擲回例外狀況。
請參閱[c + + Core Guidelines:F.6:如果您的函式可能不會擲回，將它宣告 noexcept](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)。

## <a name="concurrency-group"></a>並行存取群組

[C26441 NO_UNNAMED_GUARDS](C26441.md)必須命名為物件。 請參閱[c + + 核心指南 cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks)。

## <a name="const-group"></a>CONST 的群組

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md)函式 '%函式 %' 的參考引數 '%引數 %' 可標示為`const`。 請參閱[c + + 核心指南 con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref)。

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md):函式 '%函式 %' 的指標引數 '%引數 %' 可標示為指標`const`。 請參閱[c + + 核心指南 con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref)。

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md)指向的 '%變數 %' 的值會指派一次、 將它標示為指標`const`。 請參閱[c + + 核心指南 con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)。

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md)陣列 '%陣列 %' 的項目指派一次，將元素標記`const`。 請參閱[c + + 核心指南 con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)。

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md)陣列 '%陣列 %' 的項目所指向的值會指派一次，將元素標記為指標`const`。 請參閱[c + + 核心指南 con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)。

[C26496 USE_CONST_FOR_VARIABLE](c26496.md)一次指派變數 '%變數 %'、 將其標記為`const`。 請參閱[c + + 核心指南 con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)。

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md)標記為此函式 %函式 %`constexpr`如果想要使用編譯時期評估。 請參閱[c + + Core Guidelines F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr)。

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md)可以使用此函式呼叫函式 %`constexpr`如果想要使用編譯時期評估。 請參閱[c + + 核心指南 constexpr。(con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr)。

## <a name="type-group"></a>型別群組

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md)不用`const_cast`拋棄`const`。 `const_cast` 不是必要的資訊;常數性或揮發性不是會移除這項轉換。 請參閱[c + + 核心指南 Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast)。

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md)請勿使用`static_cast`向下轉型。 從多型類型的 cast 應使用 dynamic_cast。 請參閱[c + + 核心指南 Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast)。

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md)請勿使用`reinterpret_cast`。 從 void * 的 cast 可以使用`static_cast`。 請參閱[c + + 核心指南 Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)。

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md)請勿使用`static_cast`算術轉換。 使用大括號初始化、 gsl::narrow_cast 或 gsl:: narow。 請參閱[c + + 核心指南 Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)。

[C26473 NO_IDENTITY_CAST](C26473.md)請勿所在的來源類型和目標型別都是相同的指標類型之間進行轉換。 請參閱[c + + 核心指南 Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)。

[C26474 NO_IMPLICIT_CAST](C26474.md)請勿轉換可能為隱含時，指標類型之間進行轉換。 請參閱[c + + 核心指南 Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)。

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md)不使用函式樣式 c-cast。 請參閱[c + + Core Guidelines ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast)。

[C26490 NO_REINTERPRET_CAST](c26490.md)請勿使用`reinterpret_cast`。 請參閱[c + + 核心指南 Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。

[C26491 NO_STATIC_DOWNCAST](c26490.md)請勿使用`static_cast`向下轉型。 請參閱[c + + 核心指南 Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。

[C26492 NO_CONST_CAST](c26492.md)不用`const_cast`拋棄`const`。 請參閱[c + + 核心指南 Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。

[C26493 NO_CSTYLE_CAST](c26493.md)請勿使用 c-style 轉換 （cast）。 請參閱[c + + 核心指南 Type.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。

[C26494 VAR_USE_BEFORE_INIT](c26494.md)未初始化的變數 '%變數 %'。 一律初始化物件。 請參閱[c + + 核心指南 Type.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。

[C26495 MEMBER_UNINIT](c26495.md)未初始化的變數 '%變數 %'。 一律初始化成員變數。 請參閱[c + + 核心指南 Type.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。

## <a name="bounds-group"></a>界限群組

[C26446 USE_GSL_AT](c26446.md)偏好使用`gsl::at()`而不是未檢查的註標運算子。 請參閱[c + + Core Guidelines:Bounds.4:不使用標準程式庫函式和類型沒有檢查界限](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)。

[C26481 NO_POINTER_ARITHMETIC](C26481.md)。
請勿使用指標算術。 請改用 span。 請參閱[c + + 核心指南 Bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md)只使用常數運算式的陣列索引。 請參閱[c + + 核心指南 Bounds.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md)值 %value%超出界限 （0，繫結的 %） 的變數 '%變數 %'。 只使用索引進入陣列的陣列界限內的常數運算式。 請參閱[c + + 核心指南 Bounds.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)運算式 '%expr%':沒有指標衰減陣列。 請參閱[c + + 核心指南 Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>GSL 群組

[C26445 NO_SPAN_REF](c26445.md)的參考`gsl::span`或`std::string_view`可能表示存留期問題。
請參閱[c + + 核心指南 GSL.view:檢視](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md)偏好使用`gsl::at()`而不是未檢查的註標運算子。 請參閱[c + + Core Guidelines:Bounds.4:不使用標準程式庫函式和類型沒有檢查界限](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)。

[C26448 USE_GSL_FINALLY](c26448.md)請考慮使用`gsl::finally`如果是最後一個動作。 請參閱[c + + Core Guidelines:GSL.util:公用程式](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities)。

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span`或`std::string_view`從 temporary 所建立也會失效時 temporary 已經失效。 請參閱[c + + Core Guidelines:GSL.view:檢視](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)。


## <a name="deprecated-warnings"></a>已被取代的警告

下列警告出現在早期的實驗性的規則集合的核心指南檢查工具，但現在已淘汰，並可以放心忽略。 警告會取代上述清單中的警告。

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
[使用 c + + 核心指南檢查工具](using-the-cpp-core-guidelines-checkers.md)
