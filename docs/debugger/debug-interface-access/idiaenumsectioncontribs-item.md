---
title: "Idiaenumsectioncontribs:: Item |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9338d1297263ebd55748f6438bbbec2d4ee4f044
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
透過索引擷取 > 一節的比重。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### <a name="parameters"></a>參數  
 索引  
 [in]索引的[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)要擷取的物件。 索引是在 0 到`count`-1，其中`count`傳回[idiaenumsectioncontribs:: Get_count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)方法。  
  
 section  
 [out]傳回[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)物件，代表所需的區段比重。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [Idiaenumsectioncontribs:: Get_count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)