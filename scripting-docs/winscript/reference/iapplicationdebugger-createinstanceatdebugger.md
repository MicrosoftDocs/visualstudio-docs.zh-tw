---
title: IApplicationDebugger::CreateInstanceAtDebugger |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.CreateInstanceAtDebugger
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95489464128e706e755432bee991c5481f5af8bc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425820"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
允許偵錯工具處理序中的物件來建立程式碼也就是 out-處理序偵錯工具。  
  
> [!IMPORTANT]
> 不應該實作這個方法，因為它可讓不受信任的程式碼，以建立受信任的偵錯工具執行緒任意物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CreateInstanceAtDebugger(  
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
  
 目前尚未實作方法。  
  
## <a name="see-also"></a>另請參閱  
 [IApplicationDebugger 介面](../../winscript/reference/iapplicationdebugger-interface.md)