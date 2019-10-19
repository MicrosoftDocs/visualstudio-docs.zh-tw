---
title: IActiveScriptAuthor：： AddNamedItem |Microsoft Docs
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
ms.openlocfilehash: f0d2f08a49fdc768e87152bf486ce48687c79e68
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577249"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
將根層級專案的名稱加入腳本撰寫引擎的命名空間。 *根層級專案*是可以包含屬性和方法的物件，而且也可以包含事件來源。  
  
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
 在從腳本中查看的專案名稱。 此名稱必須是唯一且持久的。  
  
 `dwFlags`  
 在與已命名專案相關聯的旗標。 可以是下列值的組合：  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|表示此專案的名稱可在腳本的命名空間中使用。 這可讓您存取專案的屬性、方法和事件。<br /><br /> 依照慣例，專案的屬性會包含專案的子成員。 因此，可以存取所有子物件屬性和方法（以及其子成員，以遞迴方式）。|  
|SCRIPTITEM_ISSOURCE|0x00000004|指出腳本可以擁有腳本事件處理常式的專案來源事件。|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|表示專案是與腳本相關聯之全域屬性和方法的集合。 其成員會撰寫為全域變數和方法。|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|表示如果已儲存腳本撰寫引擎，則應該儲存專案。|  
|SCRIPTITEM_CODEONLY|0x00000200|表示已命名的專案代表僅限程式碼的物件，而且沒有要撰寫的成員。|  
|SCRIPTITEM_NOCODE|0x00000400|表示已命名的專案只是要加入的名稱，而且沒有任何可編寫的內容。|  
  
 `pdisp`  
 在用來收集方法、屬性或事件來源之 `NamedItem` 物件的 `IDispatch`。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)