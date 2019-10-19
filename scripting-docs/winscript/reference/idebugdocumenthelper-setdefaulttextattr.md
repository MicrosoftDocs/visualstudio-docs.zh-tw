---
title: IDebugDocumentHelper：： SetDefaultTextAttr |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDefaultTextAttr
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDefaultTextAttr
ms.assetid: 019a4191-0019-4376-bf70-89b33e7369de
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea63f028497f1eb90803f59423f608d0a42960cf
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574641"
---
# <a name="idebugdocumenthelpersetdefaulttextattr"></a>IDebugDocumentHelper::SetDefaultTextAttr
設定要用於不在腳本區塊中之文字的預設屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetDefaultTextAttr(  
   SOURCE_TEXT_ATTR  staTextAttr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `staTextAttr`  
 預設的來源文字屬性。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 除非此方法變更了預設屬性，否則腳本區塊外部文字的預設屬性會是 SOURCETEXT_ATTR_NONSOURCE。 使用者介面可以使用此資訊，將腳本區塊以外的文字標示為唯讀。  
  
## <a name="see-also"></a>請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [SOURCE_TEXT_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)