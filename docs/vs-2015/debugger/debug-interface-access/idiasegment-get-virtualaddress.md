---
title: 'Idiasegment:: Get_virtualaddress |Microsoft Docs'
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
- IDiaSegment::get_virtualAddress method
ms.assetid: 30073dd0-c864-4c4a-8863-80f243419f6c
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5aae2fa927161caf51572543e1257e70e430ed9c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819702"
---
# <a name="idiasegmentgetvirtualaddress"></a>IDiaSegment::get_virtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取區段開頭的虛擬位址 (VA)。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_virtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回區段開頭的 VA。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)



