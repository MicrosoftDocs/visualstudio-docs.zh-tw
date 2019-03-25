---
title: IRemoteDebugApplication::CreateInstanceAtApplication | Microsoft Docs
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
ms.openlocfilehash: 6e17c5abcb21bfaad6de948c3676d29232da66cf
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146288"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
允許物件來建立應用程式處理序中，由程式碼也就是外處理應用程式。  
  
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
 [in]類別要建立之物件的識別項 (CLSID)。  
  
 `pUnkOuter`  
 [in]如果`NULL`，該物件尚未建立為彙總的一部分。 否則，請`pUnkOuter`彙總物件的指標`IUnknown`介面 (控制`IUnknown`)。  
  
 `dwClsContext`  
 [in]執行可執行程式碼的內容。 值取自列舉`CLSCTX`。  
  
 `riid`  
 [in]用來與物件通訊的介面識別項。  
  
 `ppvObject`  
 [out]接收要求中的介面指標的指標變數的位址`riid`。 在成功傳回時，*`ppvObject`包含要求的介面指標。 發生錯誤時， \* `ppvObject`包含`NULL`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會委派至`CoCreateInstance`。  
  
## <a name="see-also"></a>另請參閱  
 [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)