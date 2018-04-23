---
title: IDebugProcess2::GetAttachedSessionName |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 34e404fe33858c1db7d9dfb103df7b4e0bb9fb91
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
取得正在偵錯此處理程序之工作階段的名稱。 這項資訊可以顯示一個 IDE 正在偵錯特定電腦上的特定處理程序的使用者。  
  
> [!NOTE]
>  這個方法已被取代，而且它的實作應該會一律傳回`E_NOTIMPL`。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrSessionName`  
  
## <a name="return-value"></a>傳回值  
 這個方法一律會傳回`E_NOTIMPL`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)