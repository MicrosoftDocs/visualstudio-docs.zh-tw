---
title: "IDebugCoreServer2::EnumPorts |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer2::EnumPorts
helpviewer_keywords: IDebugCoreServer2::EnumPorts
ms.assetid: 3d98dfd0-614f-4d68-90c6-8a9b9cab66f1
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d22a819393f4feaf07edc535a1c0c2729af3984f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcoreserver2enumports"></a>IDebugCoreServer2::EnumPorts
擷取所有可用的連接埠清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumPorts(   
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```csharp  
int EnumPorts(   
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppEnum`  
 [out]傳回[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)物件，其中包含的所有連接埠供應商提供的所有連接埠清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)