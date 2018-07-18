---
title: 使用 Windows 執行階段 API 時的考量 | Microsoft Docs
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
- JavaScript, Windows Runtime API
ms.assetid: 2f56d70c-c80d-4876-8e6a-8ae031d31c22
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 693b3dac9def5533417638c3ec1c0de8db1d5fe3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24571468"
---
# <a name="considerations-when-using-the-windows-runtime-api"></a>使用 Windows 執行階段 API 時的考量
在 JavaScript 中，您幾乎可以使用 Windows 執行階段 API 的所有項目。 不過，您應該記住之 Windows 執行階段項目的 JavaScript 表示有一些層面。  
  
> [!IMPORTANT]
>  如需在 C++、C# 或 Visual Basic 中建立 Windows 執行階段元件以及在 JavaScript 中使用它們的資訊，請參閱[在 C++ 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)和[在 C++ 和 Visual Basic 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)。  
  
## <a name="special-cases-in-the-javascript-representation-of-windows-runtime-types"></a>以 JavaScript 表示 Windows 執行階段類型的特殊案例  
  
-   字串：未初始化字串會傳遞給 Windows 執行階段方法作為字串 "undefined"，而設定為 `null` 的字串則會傳遞為字串 "null" (只要將 `null` 或 `undefined` 值強制轉型為字串，就是這種情況)。將字串傳遞給 Windows 執行階段方法之前，應該將它初始化為空字串 ("")。  
  
-   介面：您無法在 JavaScript 中實作 Windows 執行階段介面。  
  
-   陣列：無法調整 Windows 執行階段陣列大小，因此在 JavaScript 中調整陣列大小的方法無法作用於 Windows 執行階段陣列。  
  
-   陣列：如果您將 JavaScript 陣列值傳遞給 Windows 執行階段方法，則會複製陣列。 Windows 執行階段方法無法修改陣列或其成員，也無法將它傳回給 JavaScript 應用程式。 不過，您可以使用無法複製的類型陣列 (例如，[Int32Array 物件](../javascript/reference/int32array-object.md))。  
  
-   結構：Windows 執行階段結構是 JavaScript 中的物件。 如果您想要將 Windows 執行階段結構傳遞給 Windows 執行階段方法，請不要使用 `new` 關鍵字具現化結構。 相反地，建立物件，並新增相關的成員和其值。 成員名稱應該是駝峰式命名法：`SomeStruct.firstMember`。  
  
-   物件：JavaScript 物件未與 Managed 程式碼物件 (`System.Object`) 相同。 您無法將 JavaScript 物件傳遞給需要 `System.Object` 的 Windows 執行階段方法。  
  
-   物件識別：在大部分情況下，於 Windows 執行階段與 JavaScript 之間來回傳遞的物件並不會變更。 JavaScript 引擎會維護已知物件的對應。 從 Windows 執行階段傳回物件時，會將它與地圖進行比對，並在不存在時建立新的物件。 如果物件表示 Windows 執行階段方法所傳回的介面，則遵循相同的程序。 有兩種類型的例外狀況：  
  
    -   如果物件是透過 Windows 執行階段呼叫所傳回，接著再新增新的 (expando) 屬性，則在傳遞回 Windows 執行階段時不會保留其新的屬性。 不過，將它們傳回至 JavaScript 應用程式時，因為它們與現有物件相符，所以傳回的物件沒有 expando 屬性。  
  
    -   Windows 執行階段中的結構和委派不能識別為與先前用過的結構或委派相同。 每次傳回結構或委派時，都會取得新的參考。  
  
-   名稱衝突：多個 Windows 執行階段介面可能會有同名的成員。 如果將它們合併成單一 JavaScript 物件 (這可以是執行階段類別或介面的表示)，則會表示具有完整名稱的成員。 您可以使用下列語法來呼叫這些成員：`Class["MemberName"](parameter)`。  
  
     在下列程式碼中，兩個介面具有 Draw 方法，而且執行階段類別會實作這兩個介面。  
  
    ```cpp#  
    namespace CollisionExample {  
        interface InterfaceA  
        {  
            HRESULT Draw([in] Int32 a);  
        }  
        interface InterfaceB  
        {  
            HRESULT Draw([in] HString a);  
        }  
        runtimeclass ExampleObject {  
          interface InterfaceA  
          interface InterfaceB  
        }  
    }  
    ```  
  
     以下是如何在 JavaScript 中呼叫上述程式碼。  
  
    ```JavaScript  
    var example = new ExampleObject();  
    example["CollisionExample.InterfaceA.draw"](12);  
    example["CollisionExample.InterfaceB.draw"]("hello");  
    ```  
  
-   `Out` 參數：如果 Windows 執行階段方法有多個 `out` 參數，則在 JavaScript 中，方法會將 JavaScript 物件作為其傳回值，而且物件具有對應至 `out` 參數的屬性。 例如，在 C++ 中，請考慮下列 Windows 執行階段簽章。  
  
    ```cpp#  
    void ExampleMethod(  
      [OutAttribute] char^ first,   
      [OutAttribute] char^ second  
    )  
    ```  
  
     此簽章的 JavaScript 版本是：  
  
    ```JavaScript  
    var returnValue = exampleMethod();  
  
    ```  
  
     在此範例中，`returnValue` 是具有兩個欄位的 JavaScript 物件：`first` 和 `second`。  
  
-   靜態成員：Windows 執行階段同時定義靜態成員和執行個體成員。 在 JavaScript 中，會將靜態成員新增至與 Windows 執行階段類別或介面建立關聯的物件。  
  
    ```JavaScript  
    // Static method.   
    var accel = Windows.Devices.Sensors.Accelerometer.getDefault();   
    // Instance method.   
    var reading = accel.getCurrentReading();            
    ```  
  
 如需以 JavaScript 表示 Windows 執行階段基本類型的詳細資訊，請參閱[以 JavaScript 表示 Windows 執行階段類型](../jswinrt/javascript-representation-of-windows-runtime-types.md)。