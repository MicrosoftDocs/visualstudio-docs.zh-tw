---
title: IEnumDebugProcesses2::Skip |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugProcesses2::Skip
helpviewer_keywords:
- IEnumDebugProcesses2::Skip
ms.assetid: b9e9d888-189b-44c4-a65f-e91612458898
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: be1a34628fa6a7efae6c4d14f62ab2d265e7f428
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>請參閱  
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)