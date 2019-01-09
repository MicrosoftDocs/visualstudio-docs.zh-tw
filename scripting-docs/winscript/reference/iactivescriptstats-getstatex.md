---
title: IActiveScriptStats::GetStatEx |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 824546b64323f7fb88c4ec016f8420169afa665c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097327"
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
傳回自訂指令碼統計資料。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>參數  
 `guid`  
 [in]指定要傳回的統計資料。 語意的統計資料對應至特定 GUID 完全是定義的引擎。  
  
 `pluHi`  
 [out]表示統計資料的 64 位元不帶正負號的整數高 32 位元。  
  
 `pluLo`  
 [out]表示統計資料的 64 位元不帶正負號的整數低 32 位元。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|未實作方法。|  
  
## <a name="remarks"></a>備註  
 這個方法可讓傳回自訂主機都有意義的統計資料的自訂指令碼引擎。  
  
> [!NOTE]
>  這個方法目前尚未實作。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [IActiveScriptStats 介面](../../winscript/reference/iactivescriptstats-interface.md)