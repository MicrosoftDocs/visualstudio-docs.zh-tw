---
title: 'Idiaframedata:: Get_addresssection |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_addressSection method
ms.assetid: e4eedede-4a1c-4da2-a812-b92df328fd8d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fd246ce9f547f72936a899602c439d1afcd05a45
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911430"
---
# <a name="idiaframedatagetaddresssection"></a>IDiaFrameData::get_addressSection
擷取框架的程式碼位址中區段的一部分。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回框架的程式碼位址中區段的一部分。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)