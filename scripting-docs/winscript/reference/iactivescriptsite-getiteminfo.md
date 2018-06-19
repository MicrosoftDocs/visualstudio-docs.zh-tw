---
title: IActiveScriptSite::GetItemInfo |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ccb898c14571d1f1fd1fcae7cb0b9a6d322f2754
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725418"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
可讓指令碼引擎來取得有關使用新增的項目[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrName`  
 [in]使用指定的項目，在相關聯的名稱[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)方法。  
  
 `dwReturnMask`  
 [in]位元遮罩，指定應傳回哪些項目的資訊。 指令碼引擎應該要求的最小數量的資訊，因為部分傳回參數 (例如， `ITypeInfo`) 可能需要相當長的時間才能載入或產生。 可以是下列值的組合：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|傳回`IUnknown`此項目的介面。|  
|SCRIPTINFO_ITYPEINFO|傳回`ITypeInfo`此項目的介面。|  
  
 `ppunkItem`  
 [out]收到的指標變數的位址`IUnknown`與指定的項目相關聯的介面。 可以使用指令碼引擎`IUnknown::QueryInterface`方法，以取得`IDispatch`項目的介面。 如果這個參數會接收 NULL`dwReturnMask`不包含 SCRIPTINFO_IUNKNOWN 值。 此外，它會接收 NULL 如果沒有相關聯的項目 name; 的物件這項機制用來建立簡單的類別，加入 SCRIPTITEM_CODEONLY 旗標設定的具名項目時[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)方法。  
  
 `ppTypeInfo`  
 [out]收到的指標變數的位址`ITypeInfo`與項目相關聯的介面。 如果這個參數會接收 NULL`dwReturnMask`不包含 SCRIPTINFO_ITYPEINFO 值中，或如果無法使用此項目的型別資訊。 如果未提供型別資訊，物件無法來源事件，而且必須與實現名稱繫結`IDispatch::GetIDsOfNames`方法。 請注意，`ITypeInfo`介面擷取說明的項目 coclass (TKIND_COCLASS)，因為此物件可能支援多個介面和事件介面。 如果項目支援`IProvideMultipleTypeInfo`介面，`ITypeInfo`介面擷取等同於索引以零為`ITypeInfo`，會使用取得`IProvideMultipleTypeInfo::GetInfoOfIndex`方法。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了無效的指標。|  
|`TYPE_E_ELEMENTNOTFOUND`|找不到指定之名稱的項目。|  
  
## <a name="remarks"></a>備註  
 這個方法會擷取所指定的資訊`dwReturnMask`參數; 這樣可以改善效能。 例如，如果`ITypeInfo`介面不需要的項目，它只是中未指定`dwReturnMask`。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)