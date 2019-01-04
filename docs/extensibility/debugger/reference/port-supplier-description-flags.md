---
title: PORT_SUPPLIER_DESCRIPTION_FLAGS |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- PORT_SUPPLIER_DESCRIPTION_FLAGS enumeration
ms.assetid: 5acee0ee-3a20-41c9-a7dc-0dadae6a5ba5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0db1d83a9e4f41ae349da121300d4f45284836ca
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893167"
---
# <a name="portsupplierdescriptionflags"></a>PORT_SUPPLIER_DESCRIPTION_FLAGS
定義可以擷取有關連接埠提供者的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS  
{  
   PSDFLAG_SHOW_WARNING_ICON = 0x1  
};  
typedef DWORD PORT_SUPPLIER_DESCRIPTION_FLAGS;  
```  
  
```csharp  
public enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS  
{  
   PSDFLAG_SHOW_WARNING_ICON = 0x1  
};  
```  
  
## <a name="terms"></a>詞彙  
 PSDFLAG_SHOW_WARNING_ICON  
 如果選取，警告圖示將會顯示在 UI 中。  
  
## <a name="remarks"></a>備註  
 這個列舉型別由[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭：Msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)