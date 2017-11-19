---
title: "IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetTypeFromTypeDef
- IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
ms.assetid: 7f6cd3d3-f4da-4893-be91-8dd104be8010
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4ff4d4df3051719e62af2b0a2fad8a238387ba5b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdynamicfieldcomplusgettypefromtypedef"></a>IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
擷取類型，提供的語彙基元。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetTypeFromTypeDef(  
   ULONG32       ulAppDomainID,  
   GUID          guidModule,  
   _mdToken      tokClass,  
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetTypeFromTypeDef(  
   uint            ulAppDomainID,  
   Guid            guidModule,  
   int             tokClass,  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ulAppDomainID`  
 [in]應用程式定義域的識別項。  
  
 `guidModule`  
 [in]模組的唯一識別碼。  
  
 `tokClass`  
 [in]語彙基元所代表的類型。  
  
 `ppType`  
 [out]傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)包含類型的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)