---
title: IDebugProgramNode2::GetEngineInfo |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 687ae8207fac97dde84b803fb01477d53114ad6e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847964"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
取得名稱和執行程式的偵錯引擎 (DE) 的識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetEngineInfo (   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineInfo(  
   out string pbstrEngine,   
   out Guid pguidEngine  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrEngine`  
 [out]傳回的執行程式的預設名稱 (c + + 特有： 這可以是 null 指標，指出呼叫端不想在引擎的名稱)。  
  
 `pguidEngine`  
 [out]傳回執行程式 DE 的全域唯一識別碼 (c + + 特有： 這可以是 null 指標，表示呼叫端不感興趣的引擎 GUID)。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)