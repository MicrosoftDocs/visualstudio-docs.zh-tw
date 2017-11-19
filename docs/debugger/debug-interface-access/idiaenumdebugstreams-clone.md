---
title: "Idiaenumdebugstreams:: Clone |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumDebugStreams::Clone method
ms.assetid: e85ec592-de97-4f95-a774-1623315ba415
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c46f5a006cf5201e7a0cf46be6bd9beeeabe4264
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumdebugstreamsclone"></a>IDiaEnumDebugStreams::Clone
建立列舉值，包含目前的列舉值的列舉型別狀態相同。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT Clone (   
   IDiaEnumDebugStreams** ppenum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppenum`  
 [out]傳回[IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)物件，其中包含列舉值重複。 不會有重複的資料流，此列舉值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)