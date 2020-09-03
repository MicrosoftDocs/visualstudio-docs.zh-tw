---
title: IDiaSourceFile::get_checksumType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f859bce63e2976b23ab613e249dad41b2bc63486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190705"
---
# <a name="idiasourcefileget_checksumtype"></a>IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

捕獲總和檢查碼類型。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展傳回總和檢查碼類型。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 總和檢查碼類型是可對應至總和檢查碼演算法的值。 例如，標準 PDB 檔案格式通常可以具有下列其中一個值：  
  
|總和檢查碼類型|CryptoAPI 標籤|描述|  
|-------------------|---------------------|-----------------|  
|0|\<none>|沒有任何總和檢查碼存在。|  
|1|`CALG_MD5`|使用 MD5 雜湊演算法產生的總和檢查碼。|  
|2|`CALG_SHA1`|使用 SHA1 雜湊演算法產生的總和檢查碼。|  
  
 `CryptoAPI`標籤來自 `ALG_ID` 列舉。 如需雜湊演算法的詳細資訊，請參閱 `CryptoAPI` Microsoft 的一節 [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)] 。  
  
 若要取得原始程式檔的實際總和檢查碼位元組，請呼叫 [IDiaSourceFile：： get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) 方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)
