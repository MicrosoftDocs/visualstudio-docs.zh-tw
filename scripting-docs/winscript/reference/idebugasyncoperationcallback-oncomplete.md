---
title: IDebugAsyncOperationCallBack::onComplete | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperationCallBack.onComplete
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugAsyncOperationCallBack::onComplete
ms.assetid: d4023f5a-41f9-4948-b0dc-3317d61bb783
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9e5532a55901d8e29addfee58594645440991f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821868"
---
# <a name="idebugasyncoperationcallbackoncomplete"></a>IDebugAsyncOperationCallBack::onComplete
結果是可從非同步偵錯作業的訊號。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 此方法可讓您表示結果是可從`IDebugAsyncOperation`物件。 在 偵錯工具執行緒就會引發事件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugAsyncOperationCallBack Interface](../../winscript/reference/idebugasyncoperationcallback-interface.md)   
 [IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)