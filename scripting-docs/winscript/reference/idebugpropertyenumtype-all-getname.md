---
title: IDebugPropertyEnumType_All::GetName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All.GetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All::GetName
ms.assetid: 24bbe4d5-4263-48d0-8e8d-bff957ffcad2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41eed5e7fd8ba2874250abf60826bc59da1763df
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923520"
---
# <a name="idebugpropertyenumtypeallgetname"></a>IDebugPropertyEnumType_All::GetName
傳回包含名稱的 BSTR `EnumType`。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetName(  
   BSTR*  pname  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pname`  
 [out]包含名稱的 BSTR `EnumType`。  
  
## <a name="return-value"></a>傳回值  
 會傳回有效`HRESULT`，通常是`S_OK`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPropertyEnumType_All Interface](../../winscript/reference/idebugpropertyenumtype-all-interface.md)