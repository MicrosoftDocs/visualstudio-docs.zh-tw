---
title: IActiveScriptAuthor：： RemoveTypeLib |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.RemoveTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::RemoveTypeLib
ms.assetid: 232c3698-024d-4549-8fbc-cb0d3ac17dc5
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 182d13785b20f9c5ba298ab72cd8d28977d455ba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576140"
---
# <a name="iactivescriptauthorremovetypelib"></a>IActiveScriptAuthor::RemoveTypeLib
從腳本撰寫引擎命名空間移除類型程式庫。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT RemoveTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor  
);  
```  
  
#### <a name="parameters"></a>參數  
 `rguidTypeLib`  
 在要移除之類型程式庫的 CLSID （類別識別碼）。  
  
 `dwMajor`  
 在主要版本號碼。  
  
 `dwMinor`  
 在次要版本號碼。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)