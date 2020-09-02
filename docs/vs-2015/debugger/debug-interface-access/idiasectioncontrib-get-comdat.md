---
title: IDiaSectionContrib::get_comdat | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_comdat method
ms.assetid: 8bd9be8d-59ee-4698-b055-daba354b8dcc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ddf479a2da74803916b7afc1945eb610d6b0e668
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62576629"
---
# <a name="idiasectioncontribget_comdat"></a>IDiaSectionContrib::get_comdat
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取指出區段是否為 COMDAT 記錄的旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_comdat (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展 `TRUE` 如果區段為 COMDAT 記錄，則傳回，否則傳回 `FALSE` 。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 COMDAT 記錄是 (COFF) 記錄的通用物件檔案格式，可讓連結器看到封裝的函式。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
