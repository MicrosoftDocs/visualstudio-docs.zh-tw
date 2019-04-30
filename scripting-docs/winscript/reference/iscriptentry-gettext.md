---
title: IScriptEntry::GetText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetText
ms.assetid: 105b8244-1972-4b39-ac18-965f1f345ef2
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24b314443644558b9900fc7d702dcd1b96a7cea4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787707"
---
# <a name="iscriptentrygettext"></a>IScriptEntry::GetText
傳回對應至文字`IScriptEntry`指令碼區塊或包含在原始碼`IScriptScriptlet`事件處理常式。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetText(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstr`  
 [out]中的文字`IScriptEntry`指令碼區塊或包含在原始碼`IScriptScriptlet`事件處理常式。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)