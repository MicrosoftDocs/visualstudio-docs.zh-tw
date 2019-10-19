---
title: IActiveScript：： AddNamedItem |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- AddNamedItem method, IActiveScript interface
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a343e38b944ca36da221da39832046c19b332230
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575817"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
將根層級專案的名稱加入腳本引擎的命名空間。 根層級專案是具有屬性和方法的物件、事件來源或三個。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrName`  
 在緩衝區的位址，其中包含從腳本中查看的專案名稱。 此名稱必須是唯一且持久的。  
  
 `dwFlags`  
 在與專案相關聯的旗標。 可以是這些值的組合：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|表示指定的專案代表僅限程式碼的物件，而且主控制項沒有與這個僅限程式碼物件相關聯的 `IUnknown`。 主機只有這個物件的名稱。 在之類的物件導向語言中C++，此旗標會建立類別。 並非所有語言都支援此旗標。|  
|SCRIPTITEM_GLOBALMEMBERS|指出專案是與腳本相關聯之全域屬性和方法的集合。 一般來說，腳本引擎會忽略物件名稱（而不是使用它做為[IActiveScriptSite：： GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)方法的 cookie，或用於解析明確範圍），並將其成員公開為全域變數和方法。 這可讓主機擴充可用於腳本的程式庫（執行時間函式等等）。 它會留給腳本引擎處理名稱衝突（例如，當兩個 SCRIPTITEM_GLOBALMEMBERS 專案具有相同名稱的方法時），雖然這種情況不應傳回錯誤。|  
|SCRIPTITEM_ISPERSISTENT|表示在儲存腳本引擎時，應該儲存專案。 同樣地，設定此旗標表示轉換回已初始化的狀態應該保留專案的名稱和類型資訊（不過，腳本引擎必須釋放實際物件上介面的所有指標）。|  
|SCRIPTITEM_ISSOURCE|指出腳本可以接收的專案來源事件。 子物件（本身為物件之物件的屬性）也可以將事件來源至腳本。 這不是遞迴的，但它為一般案例提供了一個方便的機制，例如，建立容器及其所有成員控制項。|  
|SCRIPTITEM_ISVISIBLE|表示專案的名稱可在腳本的命名空間中使用，允許存取專案的屬性、方法和事件。 依照慣例，專案的屬性會包含專案的子系;因此，將可存取所有的子物件屬性和方法（以及它們的子系，以遞迴方式）。|  
|SCRIPTITEM_NOCODE|表示專案只是要加入至腳本名稱空間的名稱，不應視為與程式碼相關聯的專案。 例如，如果沒有設定這個旗標，VBScript 會為命名專案建立個別的模組，而且C++可能會為命名專案建立個別的包裝函式類別。|  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了不正確指標。|  
|`E_UNEXPECTED`|不需要呼叫（例如，腳本引擎尚未載入或初始化）。|  
  
## <a name="see-also"></a>請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)