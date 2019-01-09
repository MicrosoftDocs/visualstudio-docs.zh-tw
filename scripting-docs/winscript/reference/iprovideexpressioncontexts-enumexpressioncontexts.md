---
title: IProvideExpressionContexts::EnumExpressionContexts |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2dd18408235a5621354531a2fd228ff44a19d6a1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088708"
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
>  這個方法會從感興趣的執行緒內呼叫。 它是由實作者找出目前的執行緒，並傳回適當的列舉值。  
  
## <a name="see-also"></a>另請參閱  
 [IProvideExpressionContexts 介面](../../winscript/reference/iprovideexpressioncontexts-interface.md)