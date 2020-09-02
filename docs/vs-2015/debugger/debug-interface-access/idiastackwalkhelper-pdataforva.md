---
title: IDiaStackWalkHelper::pdataForVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5af921caa989d7279bb9f52751c452d91045cf3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150088"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

傳回與虛擬位址相關聯的 .PDATA 資料區塊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>參數  
 `va`  
 在指定要取得之資料的虛擬位址。  
  
 `cbData`  
 在要取得之資料的大小（以位元組為單位）。  
  
 `pcbData`  
 擴展傳回取得的實際資料大小（以位元組為單位）。  
  
 `pbData`  
 [in，out]填入所要求資料的緩衝區。 不可以是 `NULL`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果指定的位址沒有 .pdata，則會傳回。 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 .PDATA (名為 ". .pdata" 的區段 ) 的編譯單位包含函式例外狀況處理的相關資訊。  
  
 呼叫端知道要傳回多少資料，讓呼叫端不需要要求有多少資料可供使用。 因此，如果參數為，則此方法的執行可接受傳回錯誤 `pbData` `NULL` 。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
