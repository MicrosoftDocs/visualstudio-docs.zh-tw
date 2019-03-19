---
title: IActiveScriptAuthor::AddNamedItem | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95bc529db8129c4e9af1ed9f9dc3d91de9686223
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145651"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
將指令碼撰寫引擎的命名空間中的根層級項目名稱。 A*根層級項目*是可包含屬性和方法，並也可以包含事件來源的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszName`  
 [in]從指令碼所示的項目名稱。 名稱必須是唯一且為永續性。  
  
 `dwFlags`  
 [in]具名的項目與相關聯的旗標。 可以是下列值的組合：  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|表示項目的名稱可用指令碼的命名空間中。 這可讓存取權的項目屬性、 方法和事件。<br /><br /> 依照慣例，項目的屬性會包含項目的子成員。 因此，所有子物件的屬性和方法 （和其子成員，以遞迴方式） 存取。|  
|SCRIPTITEM_ISSOURCE|0x00000004|指出指令碼可以有指令碼事件處理常式的項目來源的事件。|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|表示項目是集合的全域屬性和相關聯的指令碼的方法。 其成員被撰寫為全域變數和方法。|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|表示是否指令碼撰寫引擎會儲存，應該儲存項目。|  
|SCRIPTITEM_CODEONLY|0x00000200|表示具名的項目代表僅限程式碼的物件，而且它並沒有成員，才能撰寫。|  
|SCRIPTITEM_NOCODE|0x00000400|表示具名的項目是要加入的名稱，而且沒有什麼可以撰寫。|  
  
 `pdisp`  
 [in]`IDispatch`的`NamedItem`用來收集方法、 屬性或事件來源的物件。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)