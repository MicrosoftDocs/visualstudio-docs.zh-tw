---
title: 'Idiaenumdebugstreams:: Clone |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaEnumDebugStreams::Clone method
ms.assetid: e85ec592-de97-4f95-a774-1623315ba415
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a6f62680cc0a7007ed4c66fa8e28e8286901a86
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498546"
---
# <a name="idiaenumdebugstreamsclone"></a>IDiaEnumDebugStreams::Clone
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[idiaenumdebugstreams:: Clone](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumdebugstreams-clone)。  
  
建立列舉值，包含目前的列舉值相同的列舉型別狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumDebugStreams** ppenum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppenum`  
 [out]傳回[IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)物件，包含列舉值重複。 不重複的資料流，此列舉值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)



