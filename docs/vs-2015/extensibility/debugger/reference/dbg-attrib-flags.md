---
title: DBG_ATTRIB_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 15320fc86eab15ff59229239b28721f6e926e794
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939537"
---
# <a name="dbgattribflags"></a>DBG_ATTRIB_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

描述各種屬性，如[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)該[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)介面。 成員[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
#define DBG_ATTRIB_NONE                 0x0000000000000000,  
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,  
  
// Attributes about the object itself  
  
#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,  
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,  
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,  
  
// Attributes about the value of the object  
  
#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,  
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,  
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,  
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,  
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,  
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,  
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,  
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,  
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,  
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,  
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,  
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,  
  
// Attributes about field access types for the object  
  
#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,  
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,  
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,  
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,  
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,  
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,  
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,  
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,  
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,  
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,  
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,  
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,  
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,  
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,  
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
#define DBG_ATTRIB_DATA                 0x0000010000000000,  
#define DBG_ATTRIB_METHOD               0x0000020000000000,  
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,  
#define DBG_ATTRIB_CLASS                0x0000080000000000,  
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,  
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,  
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,  
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,  
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000  
  
typedef UINT64 DBG_ATTRIB_FLAGS;  
```  
  
```csharp  
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,  
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,  
  
// Attributes about the object itself  
  
public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,  
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,  
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,  
  
// Attributes about the value of the object  
  
public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,  
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,  
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,  
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,  
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,  
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,  
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,  
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,  
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,  
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,  
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,  
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,  
  
// Attributes about field access types for the object  
  
public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,  
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,  
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,  
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,  
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,  
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,  
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,  
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,  
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,  
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,  
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,  
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,  
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,  
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,  
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,  
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,  
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,  
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,  
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,  
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,  
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,  
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,  
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000  
```  
  
## <a name="members"></a>成員  
 DBG_ATTRIB_NONE  
 表示沒有屬性。  
  
 DBG_ATTRIB_ALL  
 表示所有屬性。  
  
 DBG_ATTRIB_OBJ_IS_EXPANDABLE  
 表示參考或屬性具有子系。  
  
 DBG_ATTRIB_OBJ_HAS_ID  
 表示已建立此物件的識別碼。  
  
 DBG_ATTRIB_OBJ_CAN_HAVE_ID  
 表示可以建立此物件的識別碼。  
  
 DBG_ATTRIB_VALUE_READONLY  
 表示值是唯讀值。  
  
 DBG_ATTRIB_VALUE_ERROR  
 表示值，會產生錯誤。  
  
 DBG_ATTRIB_VALUE_SIDE_EFFECT  
 表示評估有副作用。  
  
 DBG_ATTRIB_OVERLOADED_CONTAINER  
 表示此屬性實際上是多載的容器。  
  
 DBG_ATTRIB_VALUE_BOOLEAN  
 表示中的值`DEBUG_PROPERTY_INFO::bstrValue`是布林值。  
  
 DBG_ATTRIB_VALUE_BOOLEAN_TRUE  
 表示中的值`DEBUG_PROPERTY_INFO::bstrValue`是布林值和`TRUE`。  
  
 DBG_ATTRIB_VALUE_INVALID  
 表示 `DEBUG_PROPERTY_INFO::bstrValue` 中的值無效。  
  
 DBG_ATTRIB_VALUE_NAT  
 表示中的值`DEBUG_PROPERTY_INFO::bstrValue`是 「*不是一個東西*」 (NAT)。 NAT 描述 Intel 64 位元處理器暫存器旗標，指出延後的推測性例外狀況。  
  
 DBG_ATTRIB_VALUE_AUTOEXPANDED  
 表示中的值`DEBUG_PROPERTY_INFO::bstrValue`可能已自動展開。  
  
 DBG_ATTRIB_VALUE_TIMEOUT  
 表示，評估已逾時。  
  
 DBG_ATTRIB_VALUE_RAW_STRING  
 表示中的值`DEBUG_PROPERTY_INFO::bstrValue`可以由原始字串。  
  
 DBG_ATTRIB_VALUE_CUSTOM_VIEWER  
 表示此屬性具有至少一個與其相關聯的自訂檢視器。  
  
 DBG_ATTRIB_ACCESS_NONE  
 表示物件沒有`public`， `private`，也不`protected`輸入存取。  
  
 DBG_ATTRIB_ACCESS_PUBLIC  
 表示具有公用存取的物件。  
  
 DBG_ATTRIB_ACCESS_PRIVATE  
 表示具有私用存取的物件。  
  
 DBG_ATTRIB_ACCESS_PROTECTED  
 表示具有保護存取的物件。  
  
 DBG_ATTRIB_ACCESS_FINAL  
 表示具有最終存取的物件。  
  
 DBG_ATTRIB_ACCESS_ALL  
 若要擷取的存取屬性的遮罩`DBG_ATTRIB_FLAGS`。  
  
 DBG_ATTRIB_STORAGE_NONE  
 表示沒有指定的儲存體類型。  
  
 DBG_ATTRIB_STORAGE_GLOBAL  
 表示全域儲存體。  
  
 DBG_ATTRIB_STORAGE_STATIC  
 表示靜態儲存體。  
  
 DBG_ATTRIB_STORAGE_REGISTER  
 表示在暫存器中的儲存體。  
  
 DBG_ATTRIB_STORAGE_ALL  
 遮罩，以擷取儲存體屬性，從`DBG_ATTRIB_FLAGS`。  
  
 DBG_ATTRIB_TYPE_NONE  
 表示沒有任何型別修飾詞。  
  
 DBG_ATTRIB_TYPE_VIRTUAL  
 表示物件的型別是虛擬。  
  
 DBG_ATTRIB_TYPE_CONSTANT  
 表示物件類型是常數。  
  
 DBG_ATTRIB_TYPE_SYNCHRONIZED  
 表示物件的型別同步處理。  
  
 DBG_ATTRIB_TYPE_VOLATILE  
 表示物件的型別為 volatile。  
  
 DBG_ATTRIB_TYPE_ALL  
 若要擷取的型別屬性的遮罩`DBG_ATTRIB_FLAGS`。  
  
 DBG_ATTRIB_DATA  
 此物件表示資料欄位。  
  
 DBG_ATTRIB_METHOD  
 表示這個物件是一種方法。  
  
 DBG_ATTRIB_PROPERTY  
 表示此物件的屬性。  
  
 DBG_ATTRIB_CLASS  
 表示此物件的類別。  
  
 DBG_ATTRIB_BASECLASS  
 表示這個物件是基底類別。  
  
 DBG_ATTRIB_INTERFACE  
 表示這個物件是一種介面。  
  
 DBG_ATTRIB_INNERCLASS  
 表示這個物件是內部的類別。  
  
 DBG_ATTRIB_MOSTDERIVED  
 表示此物件是 '*最高衍生性*'。 詞彙 」*最高衍生性*"表示的實際類型的物件，而不是其參考的類型。  
  
 DBG_ATTRIB_CHILD_ALL  
 表示遮罩`DBG_ATTRIB_DATA`透過`DBG_ATTRIB_MOSTDERIVED`。  
  
 DBG_ATTRIB_MULTI_CUSTOM_VIEWERS  
 指出物件具有與它相關聯的多個自訂檢視器。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  適用於 C# 組件中未實際定義這個列舉型別中的值。 相反地，您必須將定義複製到原始程式檔中。  
  
 這些旗標也可用來做為引數傳遞時，篩選的物件，例如，子系[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)。 值可能會結合的位元`OR`。  
  
 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`旗標會指示[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]若要取得[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)從介面[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)介面及呼叫[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)如需自訂檢視器的清單。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
