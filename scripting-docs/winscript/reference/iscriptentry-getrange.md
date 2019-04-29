---
title: IScriptEntry::GetRange | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7baa284be4fa7f45f247df7f4b3d140869f254b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787733"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
傳回的起始位置和長度的項目。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pichMin`  
 [out]針對`IScriptEntry`物件，以指定指令碼區塊，會傳回 0。  
  
 針對`IScriptEntry`物件，以指定函式物件，傳回目前的指令碼區塊中的函式的起始位置。  
  
 針對`IScriptScriptlet`物件，會傳回 0。  
  
 `pcch`  
 [out]針對`IScriptEntry`物件，以指定指令碼區塊，傳回文字的長度。  
  
 針對`IScriptEntry`物件，以指定函式物件，傳回的函式定義的長度。  
  
 針對`IScriptScriptlet`物件，則會傳回項目的長度。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)