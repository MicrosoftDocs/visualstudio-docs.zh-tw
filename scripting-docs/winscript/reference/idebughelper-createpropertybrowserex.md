---
title: "IDebugHelper::CreatePropertyBrowserEx |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugHelper.CreatePropertyBrowserEx
apilocation: pdm.dll
helpviewer_keywords: IDebugHelper::CreatePropertyBrowserEx
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9bc219ea5c2ff9ff2860d36cd475985d825ae59
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
傳回屬性瀏覽器，包裝 VARIANT，並允許 VARIANT 值或 VARTYPE 類型的自訂轉換成字串。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
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
  
 `pdf`  
 [in]物件，提供自訂格式的變異。  
  
 `ppdob`  
 [out]屬性瀏覽器中。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回屬性瀏覽器，包裝 VARIANT，並允許 VARIANT 值或 VARTYPE 類型的自訂轉換成字串。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [IDebugHelper 介面](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)