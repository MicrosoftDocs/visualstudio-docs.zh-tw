---
title: "IDebugApplicationThread::SetDescription |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationThread.SetDescription
apilocation: pdm.dll
helpviewer_keywords: IDebugApplicationThread::SetDescription
ms.assetid: 084e5b74-af95-41b4-ae55-01f6f4d22168
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 941e2e5ac9843c8894a4dd83e23ab132620b8a02
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadsetdescription"></a>IDebugApplicationThread::SetDescription
設定這個執行緒的描述。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetDescription(  
   LPCOLESTR  pstrDescription  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrDescription`  
 [in]此執行緒的描述。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會設定這個執行緒的描述。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplicationThread 介面](../../winscript/reference/idebugapplicationthread-interface.md)