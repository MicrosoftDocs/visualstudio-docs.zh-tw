---
title: IActiveScriptSite：： GetItemInfo |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetItemInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c0458f42466a264c30a440b1b14a028a2457f12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570922"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
可讓腳本引擎取得以[IActiveScript：： AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)方法加入之專案的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrName`  
 在與專案相關聯的名稱，如[IActiveScript：： AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)方法中所指定。  
  
 `dwReturnMask`  
 在指定應該傳回專案相關資訊的位元遮罩。 腳本引擎應該要求最少量的資訊，因為有些傳回參數（例如 `ITypeInfo`）可能需要相當長的時間來載入或產生。 可以是下列值的組合：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|傳回此專案的 `IUnknown` 介面。|  
|SCRIPTINFO_ITYPEINFO|傳回此專案的 `ITypeInfo` 介面。|  
  
 `ppunkItem`  
 脫銷此變數的位址，會接收與指定專案相關聯之 `IUnknown` 介面的指標。 腳本引擎可以使用 `IUnknown::QueryInterface` 方法來取得專案的 `IDispatch` 介面。 如果 `dwReturnMask` 不包含 SCRIPTINFO_IUNKNOWN 值，則此參數會接收 Null。 此外，如果沒有與專案名稱相關聯的物件，它也會收到 Null;當使用[IActiveScript：： AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)方法中設定的 SCRIPTITEM_CODEONLY 旗標來新增命名專案時，會使用此機制來建立簡單的類別。  
  
 `ppTypeInfo`  
 脫銷接收與專案相關聯之 `ITypeInfo` 介面指標的變數位址。 如果 `dwReturnMask` 不包含 SCRIPTINFO_ITYPEINFO 值，或如果沒有此專案的型別資訊，此參數就會收到 Null。 如果沒有可用的類型資訊，物件就不能有來源事件，而且必須使用 `IDispatch::GetIDsOfNames` 方法來實現名稱系結。 請注意，所抓取的 `ITypeInfo` 介面會描述專案的 coclass （TKIND_COCLASS），因為物件可能支援多個介面和事件介面。 如果專案支援 `IProvideMultipleTypeInfo` 介面，則抓取的 `ITypeInfo` 介面與使用 `IProvideMultipleTypeInfo::GetInfoOfIndex` 方法取得的索引零 `ITypeInfo` 相同。  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了不正確指標。|  
|`TYPE_E_ELEMENTNOTFOUND`|找不到指定名稱的專案。|  
  
## <a name="remarks"></a>備註  
 這個方法只會抓取 `dwReturnMask` 參數所指示的資訊;這會改善效能。 例如，如果專案不需要 `ITypeInfo` 介面，則只會在 `dwReturnMask` 中指定。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)