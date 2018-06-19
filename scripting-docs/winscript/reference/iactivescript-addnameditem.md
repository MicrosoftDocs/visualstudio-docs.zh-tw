---
title: IActiveScript::AddNamedItem |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: db65361e4bde14e803d9085a4530a505ccaf9fcb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24642018"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
將指令碼引擎的命名空間的根層級項目的名稱。 根層級項目是與屬性和方法、 事件來源或這三個物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrName`  
 [in]包含的項目名稱，從指令碼檢視緩衝區的位址。 名稱必須是唯一且為永續性。  
  
 `dwFlags`  
 [in]項目相關聯的旗標。 可以是下列值的組合：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|表示具名項目代表純程式碼的物件，而且主機沒有任何`IUnknown`是僅限程式碼物件相關聯。 主機只具有此物件的名稱。 在 c + + 之類的物件導向語言，此旗標會建立類別。 並非所有語言都支援此旗標。|  
|SCRIPTITEM_GLOBALMEMBERS|表示項目是全域屬性和方法的指令碼相關聯的集合。 一般而言，指令碼引擎的物件名稱會被忽略 (而不是為了使用以 cookie 為[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)方法，或解決明確設定的範圍)，並公開其成員為全域變數和方法。 這可讓主應用程式擴充程式庫 （執行階段函式等等） 的指令碼中使用。 可處理的名稱，指令碼引擎衝突 （例如，當兩個 SCRIPTITEM_GLOBALMEMBERS 項目具有相同名稱的方法），但應該不會因為這種情況下傳回錯誤。|  
|SCRIPTITEM_ISPERSISTENT|指出應儲存項目，是否已儲存的指令碼引擎。 同樣地，這個旗標，表示初始化的狀態轉換，應該保留項目的名稱和型別資訊 （指令碼引擎必須，不過，發行所有實際的物件上的介面指標）。|  
|SCRIPTITEM_ISSOURCE|表示項目來源的指令碼可以接收的事件。 子物件 （物件的屬性，本身就是物件） 也可以來源的指令碼的事件。 這不是遞迴的但是它會提供最常見的情況下，一個方便的機制，例如建立容器和其成員的所有控制項。|  
|SCRIPTITEM_ISVISIBLE|表示項目的名稱會出現在命名空間的指令碼，以允許存取屬性、 方法和事件的項目。 依照慣例項目的屬性包含的項目子系。因此，所有子物件的屬性和方法 （和它們的子系以遞迴方式） 可存取。|  
|SCRIPTITEM_NOCODE|表示項目是直接新增至指令碼的命名空間中的名稱，而不會被視為應該用於哪些程式碼相關聯的項目。 例如，正在設定此旗標，VBScript 會建立個別的模組已命名的項目，而 c + + 可能會建立具名的項目不同的包裝函式類別。|  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_UNEXPECTED`|不應該呼叫 （例如，指令碼引擎有尚未載入或初始化）。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)