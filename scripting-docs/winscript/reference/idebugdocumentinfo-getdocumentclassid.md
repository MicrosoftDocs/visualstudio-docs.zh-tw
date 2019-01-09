---
title: IDebugDocumentInfo::GetDocumentClassId |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetDocumentClassId
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetDocumentClassId
ms.assetid: 3b858794-2c0c-42ba-b98c-cd820ebace20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65f43f3dbf76c9055bc4e521435ab56b1c7c6e40
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086758"
---
# <a name="idebugdocumentinfogetdocumentclassid"></a>IDebugDocumentInfo::GetDocumentClassId
傳回`CLSID`識別文件類型。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDocumentClassId(  
   CLSID*  pclsidDocument  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pclsidDocument`  
 [out]A`CLSID`識別文件類型。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法可讓偵錯工具 IDE 主應用程式的自訂檢視器，這份文件。  
  
 如果文件並沒有可檢視的資料，傳回值`pclsidDocument`是`CLSID_NULL`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentInfo 介面](../../winscript/reference/idebugdocumentinfo-interface.md)