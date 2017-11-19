---
title: "IDebugDocumentTextEvents::onUpdateTextAttributes |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentTextEvents.onUpdateTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentTextEvents::onUpdateTextAttributes
ms.assetid: 24a6d409-3137-4a7a-ac24-0955c109902f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ea7caa1c1632e1a85e12010ec39593b8e0a6d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttexteventsonupdatetextattributes"></a>IDebugDocumentTextEvents::onUpdateTextAttributes
表示基礎的字元位置範圍相關聯的文字屬性已變更。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT onUpdateTextAttributes(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToUpdate  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cCharacterPosition`  
 [in]屬性已變更的第一個字元的字元位置。  
  
 `cNumToUpdate`  
 [in]在範圍內的字元數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法表示基礎的字元位置範圍相關聯的文字屬性已變更。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentTextEvents 介面](../../winscript/reference/idebugdocumenttextevents-interface.md)