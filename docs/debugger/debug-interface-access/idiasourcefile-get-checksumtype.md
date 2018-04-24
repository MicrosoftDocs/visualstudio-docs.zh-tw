---
title: 'Idiasourcefile:: Get_checksumtype |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83d1aa687ec7f19df61031d4ff334751ccabaebd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
擷取的密碼總和類型。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回總和檢查碼的類型。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 總和檢查碼類型會是可對應至總和檢查碼演算法的值。 例如，標準的 PDB 檔案格式可以通常具有下列值之一：  
  
|總和檢查碼類型|CryptoAPI 標籤|描述|  
|-------------------|---------------------|-----------------|  
|0|\<無 >|不存在的總和檢查碼。|  
|1|`CALG_MD5`|使用 MD5 雜湊演算法所產生的總和檢查碼。|  
|2|`CALG_SHA1`|使用 SHA1 雜湊演算法所產生的總和檢查碼。|  
  
 `CryptoAPI`標籤是從`ALG_ID`列舉型別。 如需有關雜湊演算法的詳細資訊，請參閱`CryptoAPI`區段 Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)]。  
  
 若要取得實際的總和檢查碼位元組，原始程式檔，請呼叫[idiasourcefile:: Get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)