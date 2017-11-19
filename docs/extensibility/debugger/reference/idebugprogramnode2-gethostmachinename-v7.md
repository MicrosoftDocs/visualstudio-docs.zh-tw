---
title: "IDebugProgramNode2::GetHostMachineName_V7 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
ms.assetid: a992f2c9-f68b-4146-8cc2-027753bf7ce6
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 536fc9d8b83f21141abb1db05066232ea48382de
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramnode2gethostmachinenamev7"></a>IDebugProgramNode2::GetHostMachineName_V7
已被取代。 請勿使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetHostMachineName_V7 (   
   BSTR* pbstrHostMachineName  
);  
```  
  
```csharp  
int GetHostMachineName_V7 (   
   out string pbstrHostMachineName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrHostMachineName`  
 [out]傳回程式正在執行的電腦名稱。  
  
## <a name="return-value"></a>傳回值  
 實作應該會一律傳回`E_NOTIMPL`。  
  
## <a name="remarks"></a>備註  
  
> [!WARNING]
>  從[!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]，此方法已不再使用，而且應該會一律傳回`E_NOTIMPL`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)