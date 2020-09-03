---
title: IDiaEnumSourceFiles::Next | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Next method
ms.assetid: 83bf6317-ff39-4c5c-8987-cba34e7a6983
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fe965043ad854c31c933447452f1039ba40cd04a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189817"
---
# <a name="idiaenumsourcefilesnext"></a>IDiaEnumSourceFiles::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取列舉序列中指定的原始程式檔數目。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Next (   
   ULONG            celt,  
   IDiaSourceFile** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 celt  
 在要抓取的列舉值中的原始程式檔數目。  
  
 rgelt  
 擴展要填入 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 物件的陣列，這些物件代表所需的原始程式檔。  
  
 pceltFetched  
 擴展傳回已提取列舉值中的原始程式檔數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果沒有其他來源檔案，則會傳回。 否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession：： findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
