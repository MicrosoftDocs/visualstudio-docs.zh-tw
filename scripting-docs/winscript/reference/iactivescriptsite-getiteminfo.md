---
title: IActiveScriptSite::GetItemInfo | Microsoft Docs
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
ms.openlocfilehash: 997245f8e4fd43ac2162587f07e4c8711af7caac
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148681"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
可讓指令碼引擎，以取得與所加入的項目相關資訊[iactivescript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md)方法。  
  
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
 [in]使用指定的項目，在相關聯的名稱[iactivescript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md)方法。  
  
 `dwReturnMask`  
 [in]位元遮罩，指定應該傳回哪些項目的相關資訊。 指令碼引擎應該要求資訊的最小數量，因為部分傳回參數 (例如`ITypeInfo`) 可能需要相當長的時間才能載入或產生。 可以是下列值的組合：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|傳回`IUnknown`此項目的介面。|  
|SCRIPTINFO_ITYPEINFO|傳回`ITypeInfo`此項目的介面。|  
  
 `ppunkItem`  
 [out]收到的指標變數的位址`IUnknown`與指定的項目相關聯的介面。 可以使用指令碼引擎`IUnknown::QueryInterface`方法，以取得`IDispatch`項目的介面。 如果這個參數會接收 NULL`dwReturnMask`不包含 SCRIPTINFO_IUNKNOWN 值。 此外，它會接收 NULL 如果沒有項目名稱; 相關聯的物件這項機制用來建立簡單的類別，SCRIPTITEM_CODEONLY 旗標設定在 新增具名項目時[iactivescript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md)方法。  
  
 `ppTypeInfo`  
 [out]收到的指標變數的位址`ITypeInfo`項目相關聯的介面。 如果這個參數會接收 NULL`dwReturnMask`不包含 SCRIPTINFO_ITYPEINFO 值，或如果未提供此項目的型別資訊。 如果未提供類型資訊，物件無法來源事件，而且名稱繫結必須實現與`IDispatch::GetIDsOfNames`方法。 請注意，`ITypeInfo`介面擷取描述項目的 coclass (TKIND_COCLASS)，因為物件可能支援多個介面和事件介面。 如果項目支援`IProvideMultipleTypeInfo`介面，`ITypeInfo`擷取的介面是索引以零為相同`ITypeInfo`，會使用來取得`IProvideMultipleTypeInfo::GetInfoOfIndex`方法。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了無效的指標。|  
|`TYPE_E_ELEMENTNOTFOUND`|找不到指定之名稱的項目。|  
  
## <a name="remarks"></a>備註  
 這個方法只擷取的資訊由`dwReturnMask`參數; 這可改善效能。 例如，如果`ITypeInfo`介面不需要的項目，它只是中未指定`dwReturnMask`。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)