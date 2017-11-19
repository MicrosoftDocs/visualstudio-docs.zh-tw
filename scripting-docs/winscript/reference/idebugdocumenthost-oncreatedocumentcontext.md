---
title: "IDebugDocumentHost::OnCreateDocumentContext |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHost.OnCreateDocumentContext
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentHost::OnCreateDocumentContext
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55598a4191d421d3aea01d27cc7991b70bd6a019
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
通知主機，正在建立新的文件內容，並可讓主應用程式選擇性地傳回未知的新內容的控制。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppunkOuter`  
 [out]控制新內容的物件。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|主機並未提供控制的物件。|  
  
## <a name="remarks"></a>備註  
 這個方法可讓主應用程式加入新的功能提供協助程式的文件內容。 這個方法可能會傳回**E_NOTIMPL**或 null 的外部物件，則這個呼叫端是負責建立內容。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentHost 介面](../../winscript/reference/idebugdocumenthost-interface.md)