---
title: IDebugDynamicFieldCOMPlus：： GetTypeFromTypeDef |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetTypeFromTypeDef
- IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
ms.assetid: 7f6cd3d3-f4da-4893-be91-8dd104be8010
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 239ecc56f6d86b24dcda4e2b2191c66e1553780f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68142945"
---
# <a name="idebugdynamicfieldcomplusgettypefromtypedef"></a>IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

根據指定的權杖來抓取類型。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 在應用程式域的識別碼。  
  
 `guidModule`  
 在模組的唯一識別碼。  
  
 `tokClass`  
 在表示類型的標記。  
  
 `ppType`  
 擴展傳回包含類型的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)
