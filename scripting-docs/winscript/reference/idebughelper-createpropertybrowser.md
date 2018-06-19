---
title: IDebugHelper::CreatePropertyBrowser |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowser
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowser
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f728068b6d1db6fe70a084ae680f32a78a0a2760
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727478"
---
# <a name="idebughelpercreatepropertybrowser"></a>IDebugHelper::CreatePropertyBrowser
傳回包裝 VARIANT 屬性瀏覽器。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pvar`  
 [in]若要瀏覽的根 variant。  
  
 `bstrName`  
 [in]提供根名稱。  
  
 `pdat`  
 [in]執行緒的要求內容。 如果這個參數是 NULL，會執行任何的封送處理。  
  
 `ppdob`  
 [out]屬性瀏覽器中。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回包裝 VARIANT 屬性瀏覽器。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
 [IDebugHelper 介面](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)