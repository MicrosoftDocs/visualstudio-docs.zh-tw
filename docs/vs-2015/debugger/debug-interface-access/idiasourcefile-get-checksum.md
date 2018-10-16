---
title: 'Idiasourcefile:: Get_checksum |Microsoft Docs'
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
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 091a99c2f963e183ccfd9a8281539b16fb64eea4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49299277"
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取的總和檢查碼位元組。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cbData`  
 [in]資料緩衝區，以位元組為單位的大小。  
  
 `pcbData`  
 [out]傳回總和檢查碼位元組數目。 此參數不得為`NULL`。  
  
 `data`  
 [in、 out]緩衝區填滿的總和檢查碼位元組。 如果這個參數是`NULL`，然後`pcbData`傳回所需的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 若要判斷用來產生總和檢查碼位元組的總和檢查碼演算法的類型，請呼叫[idiasourcefile:: Get_checksumtype](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)方法。  
  
 總和檢查碼通常會產生從原始程式檔的映像，因此原始程式檔中的變更會反映在總和檢查碼位元組中的變更。 如果不相符的總和檢查碼位元組產生從載入的映像的檔案，則應該視為檔案的總和檢查碼損毀或竄改。  
  
 典型的總和檢查碼不能超過 32 個位元組的大小，但不是假設這是最大大小的總和檢查碼。 設定`data`參數來`NULL`取得擷取總和檢查碼時所需的位元組數目。 然後配置適當大小的緩衝區，並呼叫這個方法一次使用新的緩衝區。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)



