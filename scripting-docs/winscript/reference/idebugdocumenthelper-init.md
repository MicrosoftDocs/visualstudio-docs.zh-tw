---
title: IDebugDocumentHelper：： Init |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Init
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13e6379052707aa44c0fa52f4cb30db2c4c4fa99
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576868"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
`Init` 方法會使用名稱和初始屬性來初始化 debug document helper。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pda`  
 在與此檔相關聯的 debug 應用程式。  
  
 `pszShortName`  
 在以 null 終止的字串，其中包含檔的簡短名稱。  
  
 `pszLongName`  
 在以 null 終止的字串，其中包含檔的完整名稱。  
  
 `docAttr`  
 在指定文字檔案屬性。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會使用名稱和初始屬性來初始化 debug 檔協助程式。  
  
 這份檔不會出現在樹狀結構中，直到呼叫 `IDebugDocumentHelper::Attach` 為止。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentHelper：： Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT_DOC_ATTR 常數](../../winscript/reference/text-doc-attr-constants.md)