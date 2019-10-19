---
title: IDispatchEx：： GetNameSpaceParent |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNameSpaceParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNameSpaceParent method
ms.assetid: 0b077d39-2fd6-4390-8cd5-128d9b8dc90c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2f47fab9831441e72a4ef3d4332a41c08e6a108
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574075"
---
# <a name="idispatchexgetnamespaceparent"></a>IDispatchEx::GetNameSpaceParent
抓取物件的命名空間父系介面。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetNameSpaceParent(  
   IUnknown **ppunk  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppunk`  
 接收命名空間父系介面之 `IUnknown` 介面指標的位址。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`，否則會傳回 OLE 定義的錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)