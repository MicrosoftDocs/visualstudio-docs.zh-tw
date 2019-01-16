---
title: 'Idiaenumsectioncontribs:: Get_count |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::get_Count interface
ms.assetid: 94f11de3-9393-4a5c-9814-2e6bdb597f70
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3853cb49efdea54c50fa122361715d4e3d0bcf0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847807"
---
# <a name="idiaenumsectioncontribsgetcount"></a>IDiaEnumSectionContribs::get_Count
擷取區段貢獻數目。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_Count (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回一節的貢獻的數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)