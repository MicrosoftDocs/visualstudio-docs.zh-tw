---
title: IActiveScript::AddNamedItem | Microsoft Docs
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
ms.openlocfilehash: db0a97c01d948a0c26850ebd1c3f47c6e3900614
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151852"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
將指令碼引擎的命名空間中的根層級項目名稱。 根層級項目是具有屬性和方法、 事件來源或這三個物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrName`  
 [in]此緩衝區包含項目的名稱，從指令碼所示的位址。 名稱必須是唯一且為永續性。  
  
 `dwFlags`  
 [in]項目相關聯的旗標。 可以是下列值的組合：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|表示具名的項目代表僅限程式碼的物件，而且主應用程式沒有`IUnknown`是僅限程式碼的物件相關聯。 主應用程式只有這個物件的名稱。 在物件導向語言，例如 c + +，這個旗標會建立一個類別。 並非所有語言都支援此旗標。|  
|SCRIPTITEM_GLOBALMEMBERS|表示項目是全域屬性和方法指令碼相關聯的集合。 一般來說，指令碼引擎會忽略的物件名稱 (而非以使用它做為 cookie [iactivescriptsite:: Getiteminfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)方法，或解決明確範圍) 並公開其成員為全域變數和方法。 這可讓主應用程式擴充程式庫 （執行階段函式等等） 提供給指令碼。 保留指令碼引擎處理名稱發生衝突 （例如，當兩個 SCRIPTITEM_GLOBALMEMBERS 項目有相同名稱的方法），但應該不會因為這種情況下傳回錯誤。|  
|SCRIPTITEM_ISPERSISTENT|表示是否指令碼引擎已儲存，應該儲存項目。 設定這個旗標同樣地，表示轉換為初始化的狀態應該會保留項目的名稱和型別資訊 （指令碼引擎必須，但是，釋放所有介面上實際物件的指標）。|  
|SCRIPTITEM_ISSOURCE|表示項目來源的指令碼可以接收的事件。 子物件 （物件的屬性，本身就是物件） 也可以獲得指令碼的事件。 這不是遞迴的但它提供最常見的情況下，方便的機制，例如建立容器和其成員的所有控制項。|  
|SCRIPTITEM_ISVISIBLE|表示項目的名稱可用指令碼，允許存取屬性、 方法和事件之項目的命名空間中。 依照慣例項目的屬性會包含項目的子系;因此，所有子物件的屬性和方法 （和其子系，以遞迴方式） 可存取。|  
|SCRIPTITEM_NOCODE|表示的項目，只是要新增至指令碼的命名空間中的名稱，且不會視為的程式碼應該是相關聯的項目。 比方說，而不需要設定此旗標，VBScript 會建立具名的項目，個別模組和 c + + 可能會建立具名的項目不同的包裝函式類別。|  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_UNEXPECTED`|不需要呼叫 （例如，指令碼引擎有尚未載入或初始化）。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)