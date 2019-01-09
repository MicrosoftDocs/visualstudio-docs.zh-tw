---
title: 'Idebugdocumenthelper:: Init |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d4bcb64b7bbb1c61e7f031d872f7d1440fd17833
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086628"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
`Init`方法會初始化偵錯文件協助程式使用的名稱和初始屬性。  
  
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
 [in]這份文件相關的偵錯應用程式。  
  
 `pszShortName`  
 [in]以 null 結束的字串，包含文件的簡短名稱。  
  
 `pszLongName`  
 [in]以 null 結束的字串，包含文件的完整名稱。  
  
 `docAttr`  
 [in]指定文字的文件屬性。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會初始化偵錯文件協助程式使用的名稱和初始屬性。  
  
 這份文件不會出現在樹狀目錄中，直到`IDebugDocumentHelper::Attach`呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [Idebugdocumenthelper:: Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT_DOC_ATTR 常數](../../winscript/reference/text-doc-attr-constants.md)