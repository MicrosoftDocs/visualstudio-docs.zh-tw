---
title: "IDebugProperty::GetParent |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugProperty.GetParent
apilocation: scrobj.dll
helpviewer_keywords: IDebugProperty::GetParent
ms.assetid: 673d625b-acca-45c4-88f4-b72275042f8f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8559f7c7d5baa5144449f67850d2fe882c379e94
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertygetparent"></a>IDebugProperty::GetParent
取得屬性的父屬性。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetParent (  
   IDebugProperty** ppParent  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppParent`  
 [out]傳回`IDebugProperty`介面，表示屬性的父代。  
  
## <a name="return-value"></a>傳回值  
 傳回有效`HRESULT`，通常`S_OK`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)