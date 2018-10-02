---
title: IDebugProperty3::DestroyObjectID |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 012a4fcc8b5ada9208a3d2b4cd65e5e7ae5c225d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485962"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugProperty3::DestroyObjectID](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty3-destroyobjectid)。  
  
終結與這個屬性相關聯，指出呼叫端不會再想要找出此屬性唯一從所有其他屬性的唯一識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```csharp  
int DestroyObjectID();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果偵錯引擎不需要支援屬性的唯一識別碼 （因為它已經追蹤這些唯一內部），則可以只傳回`E_NOTIMPL`這個方法。  
  
 藉由呼叫會建立唯一的識別碼[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)方法，當呼叫端想要確定此屬性會唯一識別以及所有其他屬性。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)

