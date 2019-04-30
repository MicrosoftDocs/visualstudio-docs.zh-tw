---
title: 'Idebugdocumenthost:: Oncreatedocumentcontext |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.OnCreateDocumentContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::OnCreateDocumentContext
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3b614cdc6aad17ab3a4f6e83927b59390005ac2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62971091"
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
正在建立新的文件內容，並可讓主應用程式選擇性地傳回未知的新內容控制，請通知主機。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppunkOuter`  
 [out]物件可控制新的內容。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|主機並未提供控制的物件。|  
  
## <a name="remarks"></a>備註  
 這個方法可讓主應用程式加入新的功能提供協助程式文件內容。 這個方法可能會傳回**E_NOTIMPL**或 null 的外部物件，則這個呼叫者是負責建立內容。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentHost 介面](../../winscript/reference/idebugdocumenthost-interface.md)