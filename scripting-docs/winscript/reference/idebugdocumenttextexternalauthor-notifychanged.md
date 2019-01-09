---
title: IDebugDocumentTextExternalAuthor::NotifyChanged |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.NotifyChanged
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::NotifyChanged
ms.assetid: f0de7984-3a15-49e2-bd29-f768f34d2a4d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6338a4f88435f47ef33abe593c0bb4e000ae6ee2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094103"
---
# <a name="idebugdocumenttextexternalauthornotifychanged"></a>IDebugDocumentTextExternalAuthor::NotifyChanged
通知主機已變更的文件來源。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT NotifyChanged();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 之後會修改檔案為基礎的偵錯工具文件，並將其儲存以通知主機已變更的文件來源，則外部編輯器會呼叫這個方法。 主應用程式然後重新整理來自原始程式檔的文件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentTextExternalAuthor 介面](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)