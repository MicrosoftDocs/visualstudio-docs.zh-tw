---
title: IDebugHelper::CreatePropertyBrowser |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 4fc1e4365deea4a3981d9cf457a2c0af37edcd43
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158902"
---
# <a name="idebughelpercreatepropertybrowser"></a>IDebugHelper::CreatePropertyBrowser
傳回包裝 VARIANT 屬性瀏覽器。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pvar`  
 [in]若要瀏覽的根變數。  
  
 `bstrName`  
 [in]要提供根目錄的名稱。  
  
 `pdat`  
 [in]執行緒的要求內容。 如果此參數為 NULL，會執行任何封送處理。  
  
 `ppdob`  
 [out]屬性瀏覽器中。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回包裝 VARIANT 屬性瀏覽器。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
 [IDebugHelper 介面](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)