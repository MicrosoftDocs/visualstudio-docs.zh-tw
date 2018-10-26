---
title: IDebugProcessQueryProperties::QueryProperties |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProcessQueryProperties::QueryProperties
ms.assetid: 976a9962-b689-45bb-afb6-16b2c5dbc3b8
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 89bdd8106b0c80c0c598bfd4eec6ce296bb2b4eb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948261"
---
# <a name="idebugprocessquerypropertiesqueryproperties"></a>IDebugProcessQueryProperties::QueryProperties
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法會查詢偵錯的處理程序的指定的屬性值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT QueryProperties(  
   ULONG                  celt,  
   PROCESS_PROPERTY_TYPE *rgdwPropTypes,  
   VARIANT               *rgtPropValues);  
```  
  
```csharp  
int QueryProperties(  
   uint                       celt,  
   enum_PROCESS_PROPERTY_TYPE rgdwPropTypes,  
   out object[ ]              rgtPropValues);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]包含的屬性定義與屬性值的陣列的大小。  
  
 `dwPropType`  
 [in]陣列，其中包含定義之查詢的屬性。 可能值為：  
  
- PROCESS_PROPERTY_COMMAND_LINE = 1  
  
- PROCESS_PROPERTY_CURRENT_DIRECTORY = 2  
  
- PROCESS_PROPERTY_ENVIRONMENT_VARIABLES = 3  
  
  `pvarPropValue`  
  [out]包含屬性值的陣列。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 不常使用這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)

