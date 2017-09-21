---
title: "DBG_ATTRIB_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DBG_ATTRIB_FLAGS"
helpviewer_keywords: 
  - "DBGPROP_ATTRIB_FLAGS 列舉型別"
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# DBG_ATTRIB_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

說明各種不同的屬性，如[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)或[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)介面。  成員的[DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構。  
  
## 語法  
  
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
  
```c#  
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
  
## Members  
 DBG\_ATTRIB\_NONE  
 表示沒有屬性。  
  
 DBG\_ATTRIB\_ALL  
 表示所有屬性。  
  
 DBG\_ATTRIB\_OBJ\_IS\_EXPANDABLE  
 表示的屬性有子系。  
  
 DBG\_ATTRIB\_OBJ\_HAS\_ID  
 表示已建立了此物件的識別碼。  
  
 DBG\_ATTRIB\_OBJ\_CAN\_HAVE\_ID  
 表示可以建立此物件的識別碼。  
  
 DBG\_ATTRIB\_VALUE\_READONLY  
 表示值為唯讀。  
  
 DBG\_ATTRIB\_VALUE\_ERROR  
 指示值會產生錯誤。  
  
 DBG\_ATTRIB\_VALUE\_SIDE\_EFFECT  
 表示評估發生是負面的影響。  
  
 DBG\_ATTRIB\_OVERLOADED\_CONTAINER  
 表示這個屬性是真正的多載的容器。  
  
 DBG\_ATTRIB\_VALUE\_BOOLEAN  
 表示中的值`DEBUG_PROPERTY_INFO::bstrValue`是布林值。  
  
 DBG\_ATTRIB\_VALUE\_BOOLEAN\_TRUE  
 表示中的值`DEBUG_PROPERTY_INFO::bstrValue`是布林值，並`TRUE`。  
  
 DBG\_ATTRIB\_VALUE\_INVALID  
 表示中的值`DEBUG_PROPERTY_INFO::bstrValue`不正確。  
  
 DBG\_ATTRIB\_VALUE\_NAT  
 表示中的值`DEBUG_PROPERTY_INFO::bstrValue`是 「*不事*」 \(NAT\)。  NAT 會說明暫存器中的旗標 Intel 64 位元處理器，指出延後的推測性例外狀況。  
  
 DBG\_ATTRIB\_VALUE\_AUTOEXPANDED  
 表示中的值`DEBUG_PROPERTY_INFO::bstrValue`可能已經自動展開。  
  
 DBG\_ATTRIB\_VALUE\_TIMEOUT  
 指示來評估逾時。  
  
 DBG\_ATTRIB\_VALUE\_RAW\_STRING  
 表示中的值`DEBUG_PROPERTY_INFO::bstrValue`以未經處理的字串表示。  
  
 DBG\_ATTRIB\_VALUE\_CUSTOM\_VIEWER  
 表示這個屬性具有至少一個與其相關聯的自訂檢視器。  
  
 DBG\_ATTRIB\_ACCESS\_NONE  
 表示的物件具有不`public`， `private`，也不`protected`輸入存取。  
  
 DBG\_ATTRIB\_ACCESS\_PUBLIC  
 表示具有公用存取的物件。  
  
 DBG\_ATTRIB\_ACCESS\_PRIVATE  
 表示具有私用存取的物件。  
  
 DBG\_ATTRIB\_ACCESS\_PROTECTED  
 表示保護的存取權的物件。  
  
 DBG\_ATTRIB\_ACCESS\_FINAL  
 表示具有存取權的最終物件。  
  
 DBG\_ATTRIB\_ACCESS\_ALL  
 要擷取存取屬性，從遮罩`DBG_ATTRIB_FLAGS`。  
  
 DBG\_ATTRIB\_STORAGE\_NONE  
 表示未指定的儲存體類型。  
  
 DBG\_ATTRIB\_STORAGE\_GLOBAL  
 表示全域的儲存體。  
  
 DBG\_ATTRIB\_STORAGE\_STATIC  
 表示靜態存放裝置。  
  
 DBG\_ATTRIB\_STORAGE\_REGISTER  
 表示儲存在暫存器中。  
  
 DBG\_ATTRIB\_STORAGE\_ALL  
 要擷取儲存屬性，從遮罩`DBG_ATTRIB_FLAGS`。  
  
 DBG\_ATTRIB\_TYPE\_NONE  
 表示沒有型別修飾詞。  
  
 DBG\_ATTRIB\_TYPE\_VIRTUAL  
 表示物件的型別是虛擬。  
  
 DBG\_ATTRIB\_TYPE\_CONSTANT  
 表示物件的型別是常數。  
  
 DBG\_ATTRIB\_TYPE\_SYNCHRONIZED  
 表示物件的型別會同步處理。  
  
 DBG\_ATTRIB\_TYPE\_VOLATILE  
 表示物件的型別是動態的。  
  
 DBG\_ATTRIB\_TYPE\_ALL  
 若要擷取的型別屬性的遮罩`DBG_ATTRIB_FLAGS`。  
  
 DBG\_ATTRIB\_DATA  
 表示這個物件是資料欄位。  
  
 DBG\_ATTRIB\_METHOD  
 表示這個物件是一種方法。  
  
 DBG\_ATTRIB\_PROPERTY  
 表示這個物件的屬性。  
  
 DBG\_ATTRIB\_CLASS  
 表示這個物件是一種類別。  
  
 DBG\_ATTRIB\_BASECLASS  
 表示這個物件是基底類別。  
  
 DBG\_ATTRIB\_INTERFACE  
 表示這個物件的介面。  
  
 DBG\_ATTRIB\_INNERCLASS  
 表示這個物件可以是內部類別。  
  
 DBG\_ATTRIB\_MOSTDERIVED  
 表示這個物件是 '*最具衍生性*'。  這個詞彙"*最具衍生性*"表示實際物件的型別，而不其參考的型別。  
  
 DBG\_ATTRIB\_CHILD\_ALL  
 表示遮罩的`DBG_ATTRIB_DATA`到`DBG_ATTRIB_MOSTDERIVED`。  
  
 DBG\_ATTRIB\_MULTI\_CUSTOM\_VIEWERS  
 表示物件都有與其相關聯的多個自訂檢視器。  
  
## 備註  
  
> [!NOTE]
>  這個列舉型別中的值不 C\# 的組件中實際定義。  相反地，您必須將定義複製到您的原始程式檔。  
  
 這些旗標也可以用來做為引數傳遞時，篩選的物件，例如，子系[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)。  數值可以結合使用位元`OR`。  
  
 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`旗標會以指出[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]以取得[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面從[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)介面和呼叫[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)如需自訂檢視器的清單。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)