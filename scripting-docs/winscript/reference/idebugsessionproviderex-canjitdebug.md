---
title: IDebugSessionProviderEx： CanJITDebug |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSessionProviderEx:CanJITDebug
apilocation:
- scrobj.dll
ms.assetid: 68f91bed-ca69-46b5-b517-ca9ca80b8803
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1ad9192d8faac9931cd3d14e688ee2f54e46687
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574930"
---
# <a name="idebugsessionproviderexcanjitdebug"></a>IDebugSessionProviderEx:CanJITDebug
判斷是否可以使用即時偵錯工具來調試指定的進程。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CanJITDebug(  
   DWORD  pid  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pid`  
 在要進行調試之進程的處理序識別碼。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [IDebugSessionProviderEx 介面](../../winscript/reference/idebugsessionproviderex-interface.md)