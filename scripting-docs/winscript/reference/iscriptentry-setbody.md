---
title: IScriptEntry::SetBody |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetBody
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 993ffe59abb9458e1b400633430f708e7520599c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088578"
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
設定的主體中的文字`IScriptEntry`指令碼區塊或`IScriptScriptlet`程式碼片段。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>參數  
 `psz`  
 [in]針對`IScriptEntry`指令碼區塊`psz`是指令碼標記括住的文字。  
  
 針對`IScriptEntry`函式區塊`psz`是函式主體。  
  
 針對`IScriptScriptlet`物件 (衍生自`IScriptEntry`)，`psz`是程式碼片段的指令碼文字。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)