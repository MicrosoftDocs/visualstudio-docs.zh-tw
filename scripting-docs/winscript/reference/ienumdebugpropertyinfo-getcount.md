---
title: IEnumDebugPropertyInfo::GetCount |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.GetCount
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::GetCount
ms.assetid: 83a3becd-8533-4880-9c4f-193227ff25a9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06ed69926b47d8c40c3914acbd2b0208e55f709a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963438"
---
# <a name="ienumdebugpropertyinfogetcount"></a>IEnumDebugPropertyInfo::GetCount
取得數`DebugPropertyInfo`列舉值中的結構。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetCount (  
   ULONG* pcelt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcelt`  
 [out]傳回的數目`DebugPropertyInfo`列舉值中的結構。  
  
## <a name="return-value"></a>傳回值  
 會傳回有效`HRESULT`，通常是`S_OK`。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugPropertyInfo 介面](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo 結構](../../winscript/reference/debugpropertyinfo-structure.md)