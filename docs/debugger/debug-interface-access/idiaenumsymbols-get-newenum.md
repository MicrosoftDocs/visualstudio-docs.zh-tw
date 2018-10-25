---
title: 'Idiaenumsymbols:: Get__newenum |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::get__NewEnum method
ms.assetid: 879609ea-8e5a-4fa3-afa6-d24870fb4392
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5de191e718fa79ce5ed26bfc80086b7508e17fe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898339"
---
# <a name="idiaenumsymbolsgetnewenum"></a>IDiaEnumSymbols::get__NewEnum
擷取<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>這個列舉值的版本。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 pRetVal  
 [out]傳回`IUnknown`介面，表示<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>這個列舉值的版本。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)