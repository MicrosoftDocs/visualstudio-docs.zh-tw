---
title: IDebugMethodField：： Microsoft.sqlserver.replication.agentprofile.enumparameters |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8ebdd604ba97fda8751cf037e7494b59e7bb77ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162587"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

建立方法參數的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppParams`  
 擴展傳回 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 物件，代表方法的參數清單。否則，如果沒有任何參數，則會傳回 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK，如果沒有任何參數，則傳回 S_FALSE。 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 每個元素都是代表不同類型之參數的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件。 在每個物件上呼叫 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 方法，以判斷該物件代表的參數類型。  
  
 參數包含其變數名稱及其類型。 類別方法的第一個參數通常是 "this" 指標。  
  
 如果只需要參數的類型，請呼叫 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) 方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
