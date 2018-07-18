---
title: IEnumDebugProcesses2::Skip |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugProcesses2::Skip
helpviewer_keywords:
- IEnumDebugProcesses2::Skip
ms.assetid: b9e9d888-189b-44c4-a65f-e91612458898
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea66ea5574f44b241fe6406942955e7997844eb3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31124088"
---
# <a name="ienumdebugprocesses2skip"></a>IEnumDebugProcesses2::Skip
略過指定的項目數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]略過的項目數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`。 傳回`S_FALSE`如果`celt`其餘項目數目大於; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果`celt`指定的值大於數的其餘項目，列舉型別設定為結束和`S_FALSE`傳回。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)