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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68190705"
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取的總和檢查碼類型。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回總和檢查碼的類型。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 總和檢查碼型別是可以對應至總和檢查碼演算法的值。 例如，標準的 PDB 檔案格式可以通常具有下列值之一：  
  
|總和檢查碼類型|CryptoAPI 標籤|說明|  
|-------------------|---------------------|-----------------|  
|0|\<無>|不存在的總和檢查碼。|  
|1|`CALG_MD5`|使用 MD5 雜湊演算法產生的總和檢查碼。|  
|2|`CALG_SHA1`|使用 SHA1 雜湊演算法產生的總和檢查碼。|  
  
 `CryptoAPI`標籤是從`ALG_ID`列舉型別。 如需有關雜湊演算法的詳細資訊，請參閱`CryptoAPI`一節 Microsoft [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)]。  
  
 若要取得實際的總和檢查碼位元組，原始程式檔，請呼叫[idiasourcefile:: Get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)
