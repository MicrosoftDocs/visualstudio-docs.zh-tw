---
title: "IDebugCoreServer2::GetMachineName |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer2::GetName
helpviewer_keywords: IDebugCoreServer2::GetName
ms.assetid: 693bd794-7215-4f07-8651-b57366d39953
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d44fa397423d4b7c50f3eac0ae860e4c84cc938a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcoreserver2getmachinename"></a>IDebugCoreServer2::GetMachineName
取得核心伺服器執行的電腦名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName(   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrName`  
 [out]傳回字串，包含電腦的名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)