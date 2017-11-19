---
title: "IScriptEntry::GetRange |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.GetRange
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ae0ee34298e03fdd2e9c6bc841d9fbe90967e8f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
傳回的開始位置和長度的項目。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pichMin`  
 [out]如`IScriptEntry`物件，以指定指令碼區塊，會傳回 0。  
  
 如`IScriptEntry`物件，以指定的函式物件，傳回目前的指令碼區塊中的函式的起始位置。  
  
 如`IScriptScriptlet`物件，則傳回 0。  
  
 `pcch`  
 [out]如`IScriptEntry`物件，以指定指令碼區塊中，傳回文字的長度。  
  
 如`IScriptEntry`物件，以指定的函式物件，傳回的函式定義的長度。  
  
 如`IScriptScriptlet`物件，會傳回項目的長度。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)