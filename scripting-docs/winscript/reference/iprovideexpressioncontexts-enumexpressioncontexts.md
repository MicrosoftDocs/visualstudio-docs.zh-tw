---
title: IProvideExpressionContexts::EnumExpressionContexts | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProvideExpressionContexts.EnumExpressionContexts
apilocation:
- jscript.dll
helpviewer_keywords:
- IProvideExpressionContexts::EnumExpressionContexts
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 965147083bdc11a3544561fdd96cd85221ccd443
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63410143"
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
傳回這個元件的已知的運算式內容的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppedec`  
 [out]列舉值的已知此元件的運算式內容。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 處理序偵錯管理員會使用此方法來尋找與指定的執行緒相關聯的所有全域運算式內容。  
  
> [!NOTE]
> 這個方法會從感興趣的執行緒內呼叫。 它是由實作者找出目前的執行緒，並傳回適當的列舉值。  
  
## <a name="see-also"></a>另請參閱  
 [IProvideExpressionContexts 介面](../../winscript/reference/iprovideexpressioncontexts-interface.md)