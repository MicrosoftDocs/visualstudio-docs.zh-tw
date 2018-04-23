---
title: IDebugProgramPublisher2::UnpublishProgram |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9bff0c60ea8401896eb5399ed797d90b62bf0d0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
可讓無法使用，以進行偵錯的程式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT UnpublishProgram(  
   IUnknown* pDebuggeeInterface  
);  
```  
  
```csharp  
int UnpublishProgram(  
   object pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pDebuggeeInterface`  
 [in]`IUnknown`程式的介面。 這是相同的值提供給[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)方法，可唯一識別要移除的程式 （亦即，它會使用 cookie 的形式）。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 若要讓程式使用的偵錯引擎與工作階段偵錯管理員，使用[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)