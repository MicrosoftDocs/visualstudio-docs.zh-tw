---
title: IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8ff78c38ad077084b3dea9c96e3251ffddb2206
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62573010"
---
# <a name="idiastackframeget_rawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

這個方法會將指定的區域變數值視為原始位元組。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pInstance`  
 在 `IDiaLVarInstance` 物件，代表要取得其值的本機變數實例。  
  
 `cbDataMax`  
 在所指向之緩衝區中的最大位元組數目 `pbData` 。  () 最多可有8個位元組 `sizeof(ULONGLONG)` 。  
  
 `pcbData`  
 擴展傳回儲存在緩衝區中的實際位元組數目。  
  
 `pbData`  
 擴展要填入資料的緩衝區。 不可為 `NULL`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
