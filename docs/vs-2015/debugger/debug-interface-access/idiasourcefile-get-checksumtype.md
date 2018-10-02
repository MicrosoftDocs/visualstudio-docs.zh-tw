---
title: 'Idiasourcefile:: Get_checksumtype |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd51a553cab29ac7741eaa91ada356897551e12a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47492230"
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[idiasourcefile:: Get_checksumtype](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasourcefile-get-checksumtype)。  
  
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
  
|總和檢查碼類型|CryptoAPI 標籤|描述|  
|-------------------|---------------------|-----------------|  
|0|\<無 >|不存在的總和檢查碼。|  
|1|`CALG_MD5`|使用 MD5 雜湊演算法產生的總和檢查碼。|  
|2|`CALG_SHA1`|使用 SHA1 雜湊演算法產生的總和檢查碼。|  
  
 `CryptoAPI`標籤是從`ALG_ID`列舉型別。 如需有關雜湊演算法的詳細資訊，請參閱`CryptoAPI`一節 Microsoft [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)]。  
  
 若要取得實際的總和檢查碼位元組，原始程式檔，請呼叫[idiasourcefile:: Get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)



