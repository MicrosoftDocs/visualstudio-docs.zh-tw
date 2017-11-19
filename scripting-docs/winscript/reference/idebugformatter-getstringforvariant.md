---
title: "IDebugFormatter::GetStringForVariant |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugFormatter.GetStringForVariant
apilocation: jscript.dll
helpviewer_keywords: IDebugFormatter::GetStringForVariant
ms.assetid: 95189d03-1126-433e-8513-659107b3df16
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfc31b0fdbf6d1f4a29b1322dc3a3c4015f9c8ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugformattergetstringforvariant"></a>IDebugFormatter::GetStringForVariant
傳回表示指定的變數值的字串。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetStringForVariant(  
   VARIANT*  pvar,  
   ULONG     nRadix,  
   BSTR*     pbstrValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pvar`  
 [in]要表示為字串的 VARIANT。  
  
 `nRadix`  
 [in]若要使用的數字值的基數。  
  
 `pbstrValue`  
 [out]字串，代表`pvar`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回表示指定的變數值的字串。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugFormatter 介面](../../winscript/reference/idebugformatter-interface.md)