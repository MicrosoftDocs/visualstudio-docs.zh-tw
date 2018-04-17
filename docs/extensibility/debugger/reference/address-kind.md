---
title: ADDRESS_KIND |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 77fc748d77eaa46bc50b26e984de55d708db7e17
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="addresskind"></a>ADDRESS_KIND
指定的位址的種類。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
typedef DWORD ADDRESS_KIND;  
```  
  
```csharp  
public enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
```  
  
## <a name="terms"></a>詞彙  
 ADDRESS_KIND_NATIVE  
 原生位址，由[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)結構。  
  
 ADDRESS_KIND_UNMANAGED_THIS_RELATIVE  
 未受管理的位址，相對於`this`(`Me`在 Visual Basic 中) 指標而由[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)結構。  
  
 ADDRESS_KIND_UNMANAGED_PHYSICAL  
 未受管理的實體位址，由[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)結構。  
  
 ADDRESS_KIND_METHOD  
 類別方法，由[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)結構。  
  
 ADDRESS_KIND_FIELD  
 所表示的類別欄位[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)結構。  
  
 ADDRESS_KIND_LOCAL  
 位址為本機變數，而由[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)結構。  
  
 ADDRESS_KIND_PARAM  
 方法或函式，所代表之參數[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)結構。  
  
 ADDRESS_KIND_ARRAYELEM  
 陣列項目，由[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)結構。  
  
 ADDRESS_KIND_RETVAL  
 傳回值，由[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)結構。  
  
## <a name="remarks"></a>備註  
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)方法會傳回[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構，其中包含可能的結構、 等位[DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)結構。 `dwKind`欄位`DEBUG_ADDRESS_UNION`結構保存`ADDRESS_KIND`值，並說明如何解譯此等位欄位。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)