---
title: IDebugProcess2::GetAttachedSessionName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f095d72e3e008da734eb60c2193a3003624e51a4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966474"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
取得正在偵錯此處理程序之工作階段的名稱。 IDE 可以顯示這項資訊偵錯特定的電腦上特定處理序的使用者。  
  
> [!NOTE]
>  這個方法已被取代，且它的實作應該一律會傳回`E_NOTIMPL`。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrSessionName`  
  
## <a name="return-value"></a>傳回值  
 這個方法應該一律傳回`E_NOTIMPL`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)