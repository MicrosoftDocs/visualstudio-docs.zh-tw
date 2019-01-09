---
title: IScriptEntry::SetSignature |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetSignature
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 660f667d3542ff2cb9a7e96444d98b3082218a2a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089501"
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
設定類型資訊`IScriptEntry`函式物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pti`  
 [in]型別資訊。  
  
 `iMethod`  
 [in]中的方法索引`ITypeInfo`物件。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 使用設定類型資訊`IScriptEntry::SetSignature`或是[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)。 根據內部函式表示的項目也可以產生型別資訊。  
  
## <a name="see-also"></a>另請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)