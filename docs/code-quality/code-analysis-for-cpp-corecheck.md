---
title: "Visual Studio c + + 核心指導方針檢查參考 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0e12941db7f8e6f539c88014fc5fa9c55ca809c
ms.sourcegitcommit: 342e5ec5cec4d07864d65379c2add5cec247f3d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2018
---
# <a name="c-core-guidelines-checker-reference"></a>C + + 核心指導方針檢查程式參考
本節列出 c + + 核心指導方針檢查警告。 如需程式碼分析資訊，請參閱[/analyze （程式碼分析）](/cpp/build/reference/analyze-code-analysis)和[快速入門： C/c + + 程式碼分析](../code-quality/quick-start-code-analysis-for-c-cpp.md)。  
  
**請注意**： 一些警告屬於多個群組，且並非所有警告都都是參考主題。

## <a name="ownerpointer-group"></a>OWNER_POINTER Group

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)  
  如果有移動建構函式會傳回已設定領域的物件，而非堆積配置。 請參閱[c + + 核心指導方針 R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。 
     
[C26403 RESET_OR_DELETE_OWNER](C26403.md)  
  明確地刪除 擁有者或重設\<T > 指標 '%變數 %'。 請參閱[c + + 核心指導方針 R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。  
     
[C26404 DONT_DELETE_INVALID](C26404.md)  
  請勿刪除擁有者\<T > 可能處於無效狀態。 請參閱[c + + 核心指導方針 R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。  

[C26405 DONT_ASSIGN_TO_VALID](C26405.md)  
  沒有指派給擁有者\<T >，可能是處於有效狀態。 請參閱[c + + 核心指導方針 R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。  

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md)  
  請勿將原始指標指派給擁有者\<T >。 請參閱[c + + 核心指導方針 R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。  
  
[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md)  
  偏好將已設定領域的物件，所以不堆積的配置不必要地。 請參閱[c + + 核心指導方針 R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)。  

[C26429 USE_NOTNULL](C26429.md)  
  Nullness 永遠不會測試符號 '%符號 %'、 not_null 標示。 請參閱[c + + 核心指導方針 F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。  

[C26430 TEST_ON_ALL_PATHS](C26430.md)  
  符號 '%符號 %' 不被測試 nullness 上所有的路徑。 請參閱[c + + 核心指導方針 F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。  
  
[C26431 DONT_TEST_NOTNULL](C26431.md)  
  運算式 '%expr%' 的型別已 gsl::not_null。 不會測試它 nullness。 請參閱[c + + 核心指導方針 F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。  

## <a name="rawpointer-group"></a>RAW_POINTER Group
 
[C26400  NO_RAW_POINTER_ASSIGNMENT](c26400.md)  
沒有與擁有者指派的配置或函式呼叫結果\<T > 值傳回至原始指標; 使用擁有者\<T > 改為。 請參閱[c + + 核心指導方針 I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw)。 

[C26401 DONT_DELETE_NON_OWNER](c26401.md)  
無法刪除不是擁有者的原始指標\<T >。 請參閱[c + + 核心指導方針 I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw)。 

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)  是否移動建構函式會傳回已設定領域的物件，而非堆積配置。 請參閱[c + + 核心指導方針 R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)。 
 
[C26408 NO_MALLOC_FREE](C26408.md)  
  避免 malloc （） 和 free （）、 偏好的 new 與 delete 一起 nothrow 版本。 請參閱[c + + 核心指導方針 R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree)。  
  
[C26409 NO_NEW_DELETE](C26409.md)  
  避免新的呼叫和明確刪除，請使用 std::make_unique\<T > 改為。 請參閱[c + + 核心指導方針 R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete)。  

[C26429 USE_NOTNULL](C26429.md)  
  Nullness 永遠不會測試符號 '%符號 %'、 not_null 標示。 請參閱[c + + 核心指導方針 F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。  
  
[C26430 TEST_ON_ALL_PATHS](C26430.md)  
  符號 '%符號 %' 不被測試 nullness 上所有的路徑。 請參閱[c + + 核心指導方針 F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。  
  
[C26431 DONT_TEST_NOTNULL](C26431.md)  
  運算式 '%expr%' 的型別已 gsl::not_null。 不會測試它 nullness。 請參閱[c + + 核心指導方針 F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)。  
  
[C26481 NO_POINTER_ARITHMETIC](C26481.md)  
  不要使用指標算術。 請改用範圍。 請參閱[c + + 核心指導方針 Bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)。  

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)   
  運算式 '%expr%': 沒有陣列至指標衰退。 請參閱[c + + 核心指導方針 Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)。  

## <a name="uniquepointer-group"></a>UNIQUE_POINTER Group
  
[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md)  
  參數 '%參數 %' 是參考`const`唯一的指標使用 const T * 或 const T & 改為。 請參閱[c + + 核心指導方針 R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam)。  
     
[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md)  
  參數 '%參數 %' 是唯一的指標的參考，而且永遠不會重新指派或重設，使用 T * 或 T & 改為。 請參閱[c + + 核心指導方針 R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat)。  
     
[C26414 RESET_LOCAL_SMART_PTR](C26414.md)  
  移動、 複製、 重新指派，或重設本機智慧型指標 '%符號 %'。 請參閱[c + + 核心指導方針 R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)。  
    
[C26415 SMART_PTR_NOT_NEEDED](C26415.md)  
  智慧型指標參數 '符號 %' 只能用於包含存取指標。 使用 T * 或 T & 改為。 請參閱[c + + 核心指導方針 R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam)。  

## <a name="sharedpointer-group"></a>SHARED_POINTER Group

[C26414 RESET_LOCAL_SMART_PTR](C26414.md)  
  移動、 複製、 重新指派，或重設本機智慧型指標 '%符號 %'。 請參閱[c + + 核心指導方針 R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)。  
    
[C26415 SMART_PTR_NOT_NEEDED](C26415.md)  
  智慧型指標參數 '符號 %' 只能用於包含存取指標。 使用 T * 或 T & 改為。 請參閱[c + + 核心指導方針 R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam)。  
    
[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md)  
  共用的指標參數 '%符號 %' 的右值參考傳遞。 而是依值傳遞。 請參閱[c + + 核心指導方針 R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner)。  
  
[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md)  
  共用的指標參數 '%符號 %' 是傳址方式傳遞並不會重設或重新指派。 使用 T * 或 T & 改為。 請參閱[c + + 核心指導方針 R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam)。  
  
[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md)  
  共用的指標參數 '%符號 %' 不是複製或移動。 使用 T * 或 T & 改為。 請參閱[c + + 核心指導方針 R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const)。  

## <a name="declaration-group"></a>宣告群組
    
[C26426 NO_GLOBAL_INIT_CALLS](C26426.md)  
  全域初始設定式會呼叫非 constexpr 函式 '%符號 %'。 請參閱[c + + 核心指導方針 I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects)。  
  
[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md)  
  全域初始設定式會存取外部物件 '%符號 %'。 請參閱[c + + 核心指導方針 I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects)。  
  
[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md)避免未命名的物件具有自訂建構和解構。 [ES.84： 不要 （嘗試） 沒有名稱的本機變數宣告](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)。

## <a name="class-group"></a>類別群組
    
[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md)  
  如果您定義，或刪除任何類型 '%符號 %' 中的預設作業，或定義全部刪除。 請參閱[c + + 核心指導方針 C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all)。  


[C26433 OVERRIDE_EXPLICITLY](c26433.md)函式 '%符號 %' 應該以 'override' 標記。 請參閱[C.128： 虛擬函式應該指定一個虛擬的覆寫時，或最後一個](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final)。 

  
[C26434 DONT_HIDE_METHODS](C26434.md)  
  函式 '%symbol_1%' 會隱藏非虛擬函式 '%symbol_2%'。 請參閱[c + + 核心指導方針 C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final)。  
  

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md)函式 '%符號 %' 應該指定一個 'virtual'、 'override' 或 'final'。 請參閱[C.128： 虛擬函式應該指定一個虛擬的覆寫時，或最後一個](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)。 


[C26436 NEED_VIRTUAL_DTOR](C26436.md)  
  類型具有虛擬函式的 ' %符號 %' 必須是公用虛擬或受保護非虛擬解構函式。 請參閱[c + + 核心指導方針 C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual)。  


[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md)正在覆寫解構函式不應使用明確的 'override' virtual' 規範。 請參閱[C.128： 虛擬函式應該指定一個虛擬的覆寫時，或最後一個](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)。


## <a name="type-group"></a>型別群組
    
[C26437 DONT_SLICE](C26437.md)  
  不配量。 請參閱[c + + 核心指導方針 ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice)。  

## <a name="style-group"></a>樣式群組  
[C26438 NO_GOTO](C26438.md)  
  避免`goto`。 請參閱[c + + 核心指導方針 ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto)。  
  
## <a name="function-group"></a>函式群組
    
[C26439 SPECIAL_NOEXCEPT](C26439.md)  
  這種函式可能不會擲回。 將它宣告`noexcept`。 請參閱[c + + 核心指導方針 F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)。  
  
[C26440 DECLARE_NOEXCEPT](C26440.md)  
  可以宣告函式 '%符號 %' `noexcept`。 請參閱[c + + 核心指導方針 F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)。  

## <a name="concurrency-group"></a>並行存取群組
    
[C26441 NO_UNNAMED_GUARDS](C26441.md)  
 必須為防護物件。 請參閱[c + + 核心指導方針 cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks)。  

## <a name="const-group"></a>CONST 群組
    
C26460 USE_CONST_REFERENCE_ARGUMENTS  
  函式 '%函式 %1' 的參考引數 '%引數 %' 可標示為`const`。 請參閱[c + + 核心指導方針 con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref)。  
  
C26461 USE_CONST_POINTER_ARGUMENTS： 函式 '%函式 %1' 的指標引數 '%引數 %' 可標示為指標`const`。 請參閱[c + + 核心指導方針 con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref)。  
  
C26462 USE_CONST_POINTER_FOR_VARIABLE  
  '%變數 %' 所指向的值指派一次，請將它標示為指標`const`。 請參閱[c + + 核心指導方針 con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)。  
  
C26463 USE_CONST_FOR_ELEMENTS  
  陣列 '%陣列 %' 的項目都只能指派一次，標記項目`const`。 請參閱[c + + 核心指導方針 con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)。  
  
C26464 USE_CONST_POINTER_FOR_ELEMENTS  
  陣列 '%陣列 %' 的項目所指向的值只能指派一次，指標為標記項目`const`。 請參閱[c + + 核心指導方針 con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)。  

C26496 USE_CONST_FOR_VARIABLE  
  一次指派變數 '%變數 %'，請將其標記為`const`。 請參閱[c + + 核心指導方針 con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)。  
  
C26497 USE_CONSTEXPR_FOR_FUNCTION  
  此函式 %函式 %無法標示`constexpr`如果想要使用編譯時期評估。 請參閱[c + + 核心指導方針 F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr)。  
  
C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL  
  可以使用這個函式呼叫函式 %`constexpr`如果想要使用編譯時期評估。 請參閱[c + + 核心指導方針 con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr)。  

## <a name="type-group"></a>型別群組
C26465 NO_CONST_CAST_UNNECESSARY  
  請勿使用`const_cast`離開轉換`const`。 `const_cast` 不是必要的。常數性或變動不會被移除這項轉換。 請參閱[c + + 核心指導方針 Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast)。  
  
C26466 NO_STATIC_DOWNCAST_POLYMORPHIC  
  請勿使用`static_cast`向下轉型。 從多型型別轉型應該使用 dynamic_cast。 請參閱[c + + 核心指導方針 Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast)。  
  
C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR  
  請勿使用`reinterpret_cast`。 可以使用從 void * 轉換`static_cast`。 請參閱[c + + 核心指導方針 Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)。  
  
[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md)  
  請勿使用`static_cast`算術轉換。 使用大括號初始化、 gsl::narrow_cast 或 gsl::narow。 請參閱[c + + 核心指導方針 Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)。  
  
[C26473 NO_IDENTITY_CAST](C26473.md)  
  不要其中的來源類型和目標類型是相同的指標類型之間轉換。 請參閱[c + + 核心指導方針 Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)。  
  
[C26474 NO_IMPLICIT_CAST](C26474.md)  
  沒有指標類型轉換可能是隱含時之間的轉換。 請參閱[c + + 核心指導方針 Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)。  
  
[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md)  
  請勿使用函式樣式轉換 （cast） C。 請參閱[c + + 核心指導方針 ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast)。  
     
C26490 NO_REINTERPRET_CAST  
  請勿使用`reinterpret_cast`。 請參閱[c + + 核心指導方針 Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。  
  
C26491 NO_STATIC_DOWNCAST  
  請勿使用`static_cast`向下轉型。 請參閱[c + + 核心指導方針 Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。  
  
C26492 NO_CONST_CAST  
  請勿使用`const_cast`離開轉換`const`。 請參閱[c + + 核心指導方針 Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。  
    
C26493 NO_CSTYLE_CAST  
  請勿使用 c-style 轉型。 請參閱[c + + 核心指導方針 Type.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。 
     
C26494 VAR_USE_BEFORE_INIT  
  未初始化的變數 '%變數 %'。 一律初始化物件。 請參閱[c + + 核心指導方針 Type.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。  
  
C26495 MEMBER_UNINIT  
  未初始化的變數 '%變數 %'。 一律初始化成員變數。 請參閱[c + + 核心指導方針 Type.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)。  
  
## <a name="bounds-group"></a>界限群組

[C26481 NO_POINTER_ARITHMETIC](C26481.md)   
  不要使用指標算術。 請改用範圍。 請參閱[c + + 核心指導方針 Bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)。  
  
C26482 NO_DYNAMIC_ARRAY_INDEXING  
  只有使用常數運算式的陣列索引。 請參閱[c + + 核心指導方針 Bounds.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)。  
  
C26483 STATIC_INDEX_OUT_OF_RANGE  
  值 %%的值超出界限 （0、 %繫結的 %） 的變數 '%變數 %'。 只有使用陣列界限內的常數運算式的陣列索引。 請參閱[c + + 核心指導方針 Bounds.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)。  

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)   
  運算式 '%expr%': 沒有陣列至指標衰退。 請參閱[c + + 核心指導方針 Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)。  

## <a name="deprecated-warnings"></a>已被取代的警告

下列的警告會出現在早期的實驗性的規則集合的核心指導方針檢查，但現在已被取代和可以放心忽略。 警告會從上述清單的警告所取代。

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- 26422 VALID_OWNER_LEAVING_SCOPE
- 26423 ALLOCATION_NOT_ASSIGNED_TO_OWNER
- 26424 VALID_ALLOCATION_LEAVING_SCOPE
- 26425 ASSIGNING_TO_STATIC
- 26499 NO_LIFETIME_TRACKING

## <a name="see-also"></a>請參閱  
[使用 c + + 核心指導方針 Checker](using-the-cpp-core-guidelines-checkers.md)
