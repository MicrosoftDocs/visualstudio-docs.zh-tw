---
title: IScriptEntry::SetText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetText
apilocation:
- scrobj.dll
helpviewer_keywords:
- ISetEntry::SetText
ms.assetid: 4605481b-7707-43d1-ab78-a9207d0cf6fe
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17e716a7ad52cc5aeca18d02122edb9c457b14e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787628"
---
# <a name="iscriptentrysettext"></a>IScriptEntry::SetText
設定對應至文字`IScriptEntry`指令碼區塊或包含在原始碼`IScriptScriptlet`事件處理常式。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetText(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>參數  
 `psz`  
 [in]文字`IScriptEntry`指令碼區塊或原始程式碼`IScriptScriptlet`事件處理常式。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)