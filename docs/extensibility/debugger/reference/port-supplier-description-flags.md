---
title: PORT_SUPPLIER_DESCRIPTION_FLAGS |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PORT_SUPPLIER_DESCRIPTION_FLAGS enumeration
ms.assetid: 5acee0ee-3a20-41c9-a7dc-0dadae6a5ba5
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a819ff28bc7c9be1426987b3c835fd8b4e546d93
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="portsupplierdescriptionflags"></a>PORT_SUPPLIER_DESCRIPTION_FLAGS
定義可以擷取有關連接埠供應商的中繼資料。  
  
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
 如果選取，警告圖示會顯示在 UI 中。  
  
## <a name="remarks"></a>備註  
 這個列舉型別由[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)