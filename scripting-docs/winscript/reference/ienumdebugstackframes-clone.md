---
title: IEnumDebugStackFrames::Clone |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Clone
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Clone
ms.assetid: 9d9e01a3-0be3-4336-832a-f065af388571
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 978a96fdb08c460ead1b09bdc20ef6a8cf886c57
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093804"
---
# <a name="ienumdebugstackframesclone"></a>IEnumDebugStackFrames::Clone
建立列舉值，包含目前的列舉值相同的狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Clone(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppedsf`  
 [out]傳回`IEnumDebugStackFrames`複製品的列舉值的介面。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會建立包含相同的狀態，為目前的列舉值的列舉值。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugStackFrames 介面](../../winscript/reference/ienumdebugstackframes-interface.md)