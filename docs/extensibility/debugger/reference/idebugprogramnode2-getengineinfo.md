---
title: "IDebugProgramNode2::GetEngineInfo |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramNode2::GetEngineInfo
helpviewer_keywords: IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5519da3e6db7422f3b8aacca3a41a45fdff06923
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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
 [out]傳回 DE 執行程式的名稱 (c + + 特定： 這可以是 null 指標，表示呼叫端不有意引擎的名稱)。  
  
 `pguidEngine`  
 [out]傳回執行程式 DE 的全域唯一識別碼 (c + + 特定： 這可以是 null 指標，表示呼叫端不有興趣引擎的 GUID)。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)