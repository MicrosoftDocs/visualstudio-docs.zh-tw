---
title: IDebugProgram2::GetEngineInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2::GetEngineInfo
helpviewer_keywords:
- IDebugProgram2::GetEngineInfo
ms.assetid: 3a4f2dc0-e082-4d8d-aeaf-463ab09d279b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: f031cbe124765d44c116d3af35a877712cbe4502
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugprogram2getengineinfo"></a>IDebugProgram2::GetEngineInfo
Gets the name and GUID of the debug engine (DE) running this program.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetEngineInfo(   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineInfo(   
   out string pbstrEngine,  
   out GUID   pguidEngine  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pbstrEngine`  
 [out] Returns the name of the DE running this program.  
  
 `pguidEngine`  
 [out] Returns the GUID of the DE running this program.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 Each DE defines its own GUID for identification.  
  
## <a name="see-also"></a>See Also  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
