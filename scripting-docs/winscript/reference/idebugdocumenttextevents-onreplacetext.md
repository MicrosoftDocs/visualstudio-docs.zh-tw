---
title: IDebugDocumentTextEvents::onReplaceText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onReplaceText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onReplaceText
ms.assetid: 3cb053c4-1f7f-4aed-aee6-f8a9e9e69d29
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f04424eb12d0905c128913e2b0f8abe80ef5655
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089813"
---
# <a name="idebugdocumenttexteventsonreplacetext"></a>IDebugDocumentTextEvents::onReplaceText
表示已取代文字。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法表示已取代文字。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentTextEvents 介面](../../winscript/reference/idebugdocumenttextevents-interface.md)