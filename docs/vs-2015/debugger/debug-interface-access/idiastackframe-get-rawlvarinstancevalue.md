---
title: 'Idiastackframe:: Get_rawlvarinstancevalue |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c99ba92633f9cb7377252941bcabcafaf1d6242d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787623"
---
# <a name="idiastackframegetrawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

這個方法會擷取指定的本機變數的值做為未經處理位元組。  
  
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
 [in]`IDiaLVarInstance`物件，表示要取得其值的本機變數的執行個體。  
  
 `cbDataMax`  
 [in]所指向的緩衝區中的位元組數目上限`pbData`。 這最多可有 8 個位元組 (`sizeof(ULONGLONG)`)。  
  
 `pcbData`  
 [out]傳回的實際儲存在緩衝區的位元組數目。  
  
 `pbData`  
 [out]要填入資料緩衝區。 不可為 `NULL`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)



