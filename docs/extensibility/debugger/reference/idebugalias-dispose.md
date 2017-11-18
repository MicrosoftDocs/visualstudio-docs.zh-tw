---
title: "IDebugAlias::Dispose |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAlias::Dispose
helpviewer_keywords: IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d10b1e45f9970b2bf331b590f709ef0d8cd15bcd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
將標示為移除此別名。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Dispose();  
```  
  
```csharp  
int Dispose();  
```  
  
#### <a name="parameters"></a>參數  
 無。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 一旦呼叫此方法時，別名已無法再使用。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)