---
title: 'Idialinenumber:: Get_length |Microsoft Docs'
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
- IDiaLineNumber::get_length method
ms.assetid: 2c55a6f7-4ef5-45fb-9fd1-d72deaaa2829
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79657b3f7b03d7e5884cab278cf4cc46aa123033
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823667"
---
# <a name="idialinenumbergetlength"></a>IDiaLineNumber::get_length
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取在區塊中的位元組數目。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_length (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]在區塊中傳回位元組的數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 區塊是該行的原始碼的長度表示的[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)物件。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)



