---
title: "IVariantChangeType::ChangeType |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IVariantChangeType.ChangeType
apilocation: scrobj.dll
helpviewer_keywords: IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d742d1bd57c85aa75c9ccd60479d08c1a559fb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
採用變數的值，並建立新變數的指定類型。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pvarDst`  
 [in、 out]包含所代表的值為 variant `pvarSrc`，與所指定的類型，但`vtNew`。  
  
 `pvarSrc`  
 [in]若要變更成新類型的變數值。  
  
 `lcid`  
 [in]要轉換之引數，或傳出字串時使用的地區設定內容。  
  
 `vtNew`  
 [in]指定的型別`pvarDst`變成。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 `pvarDst`和`pvarSrc`引數可能會視為相等，在此情況下會覆寫原始的值。 這個方法會傳遞`pvarDst`至`VariantClear`函式，並進而`pvarDst`應為有效的值初始化。  
  
## <a name="see-also"></a>另請參閱  
 [IVariantChangeType 介面](../../winscript/reference/ivariantchangetype-interface.md)