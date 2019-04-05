---
title: IDiaEnumSectionContribs::Item | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 06a82fbb52ccdf0f9fb9fda50a74f2cfb30e7648
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943943"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

透過索引中擷取一節的貢獻。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### <a name="parameters"></a>參數  
 索引  
 [in]索引[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)要擷取的物件。 索引是在範圍介於 0 到`count`-1，其中`count`會傳回[idiaenumsectioncontribs:: Get_count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)方法。  
  
 section  
 [out]傳回[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)物件，表示所需的區段所佔的比重。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
