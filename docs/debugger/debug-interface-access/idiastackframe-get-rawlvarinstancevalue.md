---
title: "Idiastackframe:: Get_rawlvarinstancevalue |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5872c77a9154c72f6c3bcd76452792cff34452cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackframegetrawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
這個方法會擷取指定的本機變數的值做為未經處理位元組。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pInstance`  
 [in]`IDiaLVarInstance`物件，代表執行個體的本機變數，以取得的值。  
  
 `cbDataMax`  
 [in]所指向的緩衝區中的位元組數目上限`pbData`。 這最多可有 8 個位元組 (`sizeof(ULONGLONG)`)。  
  
 `pcbData`  
 [out]傳回的實際儲存在緩衝區的位元組數目。  
  
 `pbData`  
 [out]要填入資料緩衝區。 這不是`NULL`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)