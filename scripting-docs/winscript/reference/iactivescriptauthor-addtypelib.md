---
title: IActiveScriptAuthor：： AddTypeLib |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddTypeLib
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f4bbcc694b24ffafd4333f635c7cdf0c67793a7
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985332"
---
# <a name="iactivescriptauthoraddtypelib"></a>IActiveScriptAuthor::AddTypeLib
將類型程式庫加入至腳本的命名空間。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `rguidTypeLib`  
 在要加入之類型程式庫的 CLSID （類別識別碼）。  
  
 `dwMajor`  
 在主要版本號碼。  
  
 `dwMinor`  
 在次要版本號碼。  
  
 `dwFlags`  
 在未使用。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會呼叫 `LoadTypeLib` 來載入類型程式庫。 成功時，這個方法會呼叫 `IActiveScriptAuthor::AddNamedItem` 來加入型別資訊。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor：： AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)    
 [LoadTypeLib](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelib)