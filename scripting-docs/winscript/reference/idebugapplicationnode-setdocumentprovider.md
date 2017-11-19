---
title: "IDebugApplicationNode::SetDocumentProvider |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationNode.SetDocumentProvider
apilocation: pdm.dll
helpviewer_keywords: IDebugApplicationNode::SetDocumentProvider
ms.assetid: 7cb587ca-d84e-4b5e-9b94-e973cca55a03
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95c80bf04c129b2410b97b2e01861a1007457239
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodesetdocumentprovider"></a>IDebugApplicationNode::SetDocumentProvider
設定此應用程式節點的文件提供者。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetDocumentProvider(  
   IDebugDocumentProvider*  pddp  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pddp`  
 [in]此應用程式節點的文件提供者。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會設定此應用程式節點的文件提供者。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplicationNode 介面](../../winscript/reference/idebugapplicationnode-interface.md)