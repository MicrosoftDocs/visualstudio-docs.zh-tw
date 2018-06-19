---
title: 以 JavaScript 表示 Windows 執行階段類型 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Runtime types [JavaScript]
- JavaScript, Windows Runtime types
ms.assetid: f4851802-8b40-4afa-ba6c-8a162a9a43cc
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e4c21675d26bf857391d92b99b4a94637a761ca
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24571528"
---
# <a name="javascript-representation-of-windows-runtime-types"></a>以 JavaScript 表示 Windows 執行階段類型
下表描述以 JavaScript 表示 Windows 執行階段類型的方式。  
  
> [!IMPORTANT]
>  在 Internet Explorer 中執行的應用程式無法使用 Windows 執行階段功能。  
  
## <a name="windows-runtime-types-in-javascript"></a>JavaScript 中的 Windows 執行階段類型  
  
|Windows 執行階段類型|JavaScript 表示|說明|  
|--------------------------|-------------------------------|-----------------|  
|`UInt8`|`Number`|Windows 執行階段 `Uint8` 是不帶正負號的 8 位元整數，表示為 JavaScript 數字。 JavaScript 值會先轉換成 JavaScript 數字，然後遵循 `ToUint32` 程序。 如果 JavaScript 數字值超出 Uint8 範圍，則結果會套用模數 2^8。|  
|`Int32`|`Number`|Windows 執行階段 `Int32` 是帶正負號的 32 位元整數，表示為 JavaScript 數字。 JavaScript 值會先轉換成 JavaScript 數字，然後遵循 `ToInt32` 程序。 如果 JavaScript 數字值超出 `Int32` 範圍，則結果會套用模數 2^16。|  
|`Int64`|`Number`|Windows 執行階段 `Int64` 是帶正負號的 64 位元整數，如果它落在 [-2^53, 2^53] 範圍內，則表示為標準數字。 如果它落在這個範圍外部，則會表示為數字值，而數字值具有可維護完整 64 位元整數資料的自訂備份存放區。 這些自訂 Int64 數值上的所有數學運算都會導致值轉換成 [-2^53, 2^53] 範圍中的標準數字。 如果值超出這個範圍，則會引發類型錯誤。 此轉換程序的例外狀況是 `==`、`===`、`SameValue` 和 `RelationalComparison` 運算，可在傳遞兩個表示的 64 位元值時，根據完整 64 位元來比較引數。 如果其中一個引數是標準 JavaScript 數字，則這些運算也會在比較之前將引數轉換成 JavaScript 數字。 如果 JavaScript 值本身是 Int64 值，則會直接予以指派；否則，會將對值套用 `ToInteger` 轉換的結果傳遞給 Windows 執行階段。 如果類型強制型轉失敗，則會傳回例外狀況。|  
|`Uint64`|`Number`|Windows 執行階段 `Uint64` 是不帶正負號的 64 位元整數，如果它落在 [0, 2^53] 範圍內，則表示為標準數字。 如果它落在這個範圍外部，則會表示為數字，而數字具有可維護完整 64 位元不帶正負號整數資料的自訂備份存放區。 這些自訂 Uint64 值上的所有數學運算都會導致值轉換成 [0, 2^53] 範圍中的標準數字。 如果值超出這個範圍，則會引發類型錯誤。 此轉換程序的例外狀況是 `==`、`===`、`SameValue` 和 `RelationalComparison` 運算，可在傳遞兩個 64 位元值時，根據完整 64 位元來比較引數。 如果其中一個引數是標準 JavaScript 數字，則這些運算也會在比較之前將引數轉換成 JavaScript 數字。 如果 JavaScript 值本身是 Uint64 值，則會直接予以指派；否則，會將對值套用 `ToInteger` 轉換並採用模數 2^52 後的結果傳遞給 Windows 執行階段。 如果類型轉換失敗，則會傳回例外狀況。|  
|`Single`|`Number`|Windows 執行階段 `Single` 是 32 位元浮點數，透過選取與單精確度值最接近的雙精確度值以表示為 JavaScript 數字。 JavaScript 值會轉換成 JavaScript 數字，然後對其進行範圍檢查，確定值可以表示為單精確度 32 位元 IEEE 754 浮點數。 如果轉換或範圍檢查失敗，則會傳回封送處理錯誤。|  
|`Double`|`Number`|Windows 執行階段 `Double` 是 64 位元浮點數。 `ToNumber` 是用來將 Windows 執行階段 `Double` 轉換成 JavaScript 數字。 如果轉換失敗，則會傳回封送處理錯誤。|  
|`Boolean`|`Boolean`|Windows 執行階段 `Boolean` 是 8 位元值；其中，零是 `false`，而零以外的任何值是 `true`，表示為 JavaScript `Boolean`。 會先透過 `ToBoolean` 將 JavaScript 值轉換成 JavaScript `Boolean`。 這表示可以在 JavaScript 中將宣告為 `void func(BOOL);` 的 Windows 執行階段函式寫入為 `obj.func("test");`。 呼叫 Windows 執行階段函式時將 `BOOL` 參數傳遞為 `TRUE`。 如果轉換失敗，則會傳回封送處理錯誤。|  
|`Char16`|`String`|Windows 執行階段 `Char16` 是 16 位元 Unicode 字元，表示為包含單一字元的 JavaScript 字串。 透過 `ToString` 將 JavaScript 值轉換成 JavaScript 字串，然後進行檢查，確定字串的長度只有單一字元。 接著將單一字元傳遞為 `Char16` 值。 如果轉換或長度檢查失敗，則會傳回封送處理錯誤。|  
|`String`|`String`|Windows 執行階段 `String` 是不可變的 `Char16` 物件序列。 字串會表示為 JavaScript `String` 物件。 Windows 執行階段字串不會有不同的 `null` 和空字串 ("") 值。 `null` 和空字串值會轉換成 JavaScript 空字串。 注意：將 JavaScript `null` 傳遞給需要字串的 Windows 執行階段參數時，會產生字串值 "null"，而非 `null` 或空字串 ("")。 傳遞給 Windows 執行階段的字串應該一律具現化為空字串。|  
|`Enumeration`|`Object`|Windows 執行階段 `Enumeration` 是具有一組相關聯具名常數的 32 位元整數 (帶正負號或不帶正負號)。 在 JavaScript 中，列舉表示為包含每個具名值之唯讀欄位的物件。 列舉值會轉換成 JavaScript 數字，如先前針對 `Int32` 和 `UInt32` 所定義。 將 JavaScript 值轉換成 Windows 執行階段列舉時，會如前所述對其進行轉換、截斷和範圍檢查。 不過，不會根據列舉中所指定的已定義具名值來檢查產生的值。|  
|`Structure`|`Object`|Windows 執行階段 `Structure` 是具名資料欄位的異質集合。 在 JavaScript 中，結構會表示為 JavaScript 物件，其中包含結構中每個欄位的具名屬性。 如果轉換任何結構值失敗，則會傳回封送處理錯誤。 忽略 JavaScript 物件中於 Windows 執行階段結構中沒有對等項目的欄位。 注意：在 JavaScript 中，無法使用 `new` 關鍵字具現化 Windows 執行階段結構。|  
|`Array`|`Array`|Windows 執行階段 `Array` 會轉換成 JavaScript 陣列。 不過，無法調整 Windows 執行階段陣列大小，因此無法進行某些 JavaScript 陣列作業。 已轉換陣列的內部 [[Class]] 屬性未設定為 "Array"，因為 ECMAScript 5 規格不允許這項作業。 這表示 `Array.isArray(v)` 傳回 `false`。 如下將 JavaScript 值轉換成 Windows 執行階段陣列：如果值是 `null` 或 `undefined`，則會轉換成原生 `null`。 如果其內部 [[Class]] 屬性是 "Array"，則會將它複製至原生陣列，並傳遞此陣列的參考。 如前所述，如果這是轉換後的陣列，則會傳遞基礎原生陣列。 注意：將 JavaScript 陣列值傳遞給 Windows 執行階段方法，可產生陣列的完整複本。|  
|委派 (函式回呼)|`Function`|Windows 執行階段委派是單一方法的參考。 在 JavaScript 中，會將 Windows 執行階段委派表示為 JavaScript `Function`，以保證會在適當的執行緒上進行呼叫。 叫用 `Function` 時，會將引數轉換成對等 Windows 執行階段參數類型。 如果 JavaScript 引數的數目比委派 `in` 參數的數目還要少，則委派呼叫會失敗。 如果 JavaScript 引數的數目比委派中的 `in` 參數數目還要多，則會忽略額外 JavaScript 引數。 叫用委派之後，會將 `out` 參數轉換成 JavaScript 類型並傳回。 如果將原生 JavaScript 函式物件轉換成 Windows 執行階段委派，則會將它包裝在對應類型的 Windows 執行階段委派中。 叫用委派後，會將 `in` 參數轉換成 JavaScript 類型。 叫用委派之後，會將傳回值轉換成委派的 `out` 參數。|  
|介面|`Object`|介面和介面群組無法直接以 JavaScript 表示為物件。 不過，介面會表示為 Windows 執行階段方法的參數和傳回類型。 Windows 執行階段介面執行個體會如下進行轉換：<br /><br /> 1.如果具有有效的執行階段類別，則會將物件表示為該類別的執行個體。<br />2.如果沒有有效的執行階段類別，則會將物件表示為完全實作介面之未命名執行階段類別的執行個體，而執行個體已知可實作該介面和其必要介面。<br /><br /> 測試 JavaScript 值，判斷它是否為執行階段類別或介面的執行個體。 如果是，而且原始 Windows 執行階段值實作介面，則會將物件傳遞給 Windows 執行階段。|  
|執行階段類別|`Object`|Windows 執行階段中的物件可以是實作一或多個介面的執行階段類別執行個體。 在 JavaScript 中，Windows 執行階段物件會表示為物件。 類別的所有已實作介面上定義的方法、屬性和事件聯集，表示 JavaScript 物件原型中的具名屬性。 JavaScript 取用者可以直接存取類別的任何成員。 Windows 執行階段物件的原型包含來自執行階段類別之所有已實作介面的所有成員。|  
  
## <a name="see-also"></a>另請參閱  
 [在 JavaScript 中使用 Windows 執行階段](../jswinrt/using-the-windows-runtime-in-javascript.md)