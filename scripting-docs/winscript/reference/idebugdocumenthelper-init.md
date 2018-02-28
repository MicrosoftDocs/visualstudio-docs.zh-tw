---
title: "IDebugDocumentHelper::Init |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHelper.Init
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45cd57e4ba9e86bf84f927f487c637d61aa5339b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
`Init`方法初始化偵錯文件協助程式名稱，且初始屬性。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pda`  
 [in]這份文件相關聯的偵錯應用程式。  
  
 `pszShortName`  
 [in]以 null 結束的字串，包含文件的簡短名稱。  
  
 `pszLongName`  
 [in]以 null 結束的字串，包含文件的完整名稱。  
  
 `docAttr`  
 [in]指定文字文件屬性。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會初始化偵錯文件協助程式名稱，且初始屬性。  
  
 這份文件不會出現在樹狀目錄中，直到`IDebugDocumentHelper::Attach`呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT_DOC_ATTR 常數](../../winscript/reference/text-doc-attr-constants.md)