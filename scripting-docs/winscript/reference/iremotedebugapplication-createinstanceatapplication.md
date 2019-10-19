---
title: IRemoteDebugApplication：： CreateInstanceAtApplication |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.CreateInstanceAtApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::CreateInstanceAtApplication
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285e5df6960e3188ffe1ce17b1fc4f43626a3d74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572318"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
允許以跨進程的程式碼，在應用程式進程中建立物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CreateInstanceAtApplication(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `rclsid`  
 在要建立之物件的類別識別碼（CLSID）。  
  
 `pUnkOuter`  
 在如果 `NULL`，則物件不會建立為匯總的一部分。 否則，`pUnkOuter` 是匯總物件的 `IUnknown` 介面（控制 `IUnknown`）的指標。  
  
 `dwClsContext`  
 在執行可執行程式碼的內容。 值取自列舉 `CLSCTX`。  
  
 `riid`  
 在用來與物件通訊的介面識別碼。  
  
 `ppvObject`  
 脫銷指標變數的位址，會接收 `riid` 中所要求的介面指標。 成功傳回時，* `ppvObject` 包含要求的介面指標。 失敗時，\* `ppvObject` 包含 `NULL`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會委派給 `CoCreateInstance`。  
  
## <a name="see-also"></a>請參閱  
 [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)