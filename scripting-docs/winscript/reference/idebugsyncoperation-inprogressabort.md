---
title: IDebugSyncOperation::InProgressAbort |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.InProgressAbort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab8bae7f131d24c1a2c7272dc8d1178e12bf0e6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095520"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
取消進行中的作業，另一個執行緒上。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|無法取消作業。|  
|`E_ABORT`|無法完成作業。|  
  
## <a name="remarks"></a>備註  
 程序進行偵錯管理員呼叫此方法中取消的作業正在進行另一個執行緒中的偵錯工具執行緒。  
  
 如果`InProgressAbort`方法無法完成作業，它會傳回`E_ABORT`儘速。 這個方法可以傳回`E_NOTIMPL`如果無法取消作業。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugSyncOperation 介面](../../winscript/reference/idebugsyncoperation-interface.md)