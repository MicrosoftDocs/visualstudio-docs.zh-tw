---
title: IScriptEntry：： GetText |Microsoft Docs
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
ms.openlocfilehash: 2b25c1667f1df7e0394dd2ebfb0fea452da1b47d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575408"
---
# <a name="iscriptentrygettext"></a>IScriptEntry::GetText
傳回對應至 `IScriptEntry` 腳本區塊的文字，或包含在 `IScriptScriptlet` 事件處理常式中的原始程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetText(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstr`  
 脫銷@No__t_0 腳本區塊中的文字，或包含在 `IScriptScriptlet` 事件處理常式中的原始程式碼。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)