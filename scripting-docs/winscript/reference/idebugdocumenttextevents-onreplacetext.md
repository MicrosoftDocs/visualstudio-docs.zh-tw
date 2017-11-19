---
title: "IDebugDocumentTextEvents::onReplaceText |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentTextEvents.onReplaceText
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentTextEvents::onReplaceText
ms.assetid: 3cb053c4-1f7f-4aed-aee6-f8a9e9e69d29
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1cbe022113e8a97dc31b4cf5a2286ec0b5096d3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttexteventsonreplacetext"></a>IDebugDocumentTextEvents::onReplaceText
表示文字已被取代。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT onReplaceText(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToReplace  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cCharacterPosition`  
 [in]取代為第一個字元的字元位置。  
  
 `cNumToReplace`  
 [in]取代的字元數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法表示文字已被取代。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentTextEvents 介面](../../winscript/reference/idebugdocumenttextevents-interface.md)