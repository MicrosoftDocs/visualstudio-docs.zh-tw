---
title: IDebugContainerField::EnumFields |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a1fb33a65fb0bb86d3c043dd250b60b1533fed4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490453"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugContainerField::EnumFields](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcontainerfield-enumfields)。  
  
建立容器的欄位的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwKindFilter`  
 [in]組合[FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)常數，以選取要列舉的欄位。 欄位類型可以描述儲存體類型，例如類別或基本，或特定的資訊，例如本機、 參數或 「 this 」 指標。  
  
 `dwModifiersFilter`  
 [in]組合[FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)常數，以選取要列舉的欄位。 欄位修飾詞可以存取的權限，例如公用或私用或儲存體的資訊，例如虛擬、 靜態或最終。  
  
 `pszNameFilter`  
 [in]要列舉的欄位名稱。 如果所有欄位都都要傳回，這可以是 null 值。  
  
 `nameMatch`  
 [in]值，以從[NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)列舉，用於控制是否搜尋是否區分大小寫。  
  
 `ppEnum`  
 [out]傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，表示欄位的清單。 如果沒有任何欄位，則傳回 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回 S_OK 或 S_FALSE，如果沒有任何欄位。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 `dwKindFilter`， `dwModifiersFilter`，和`pszNameFilter`參數可以結合，例如，若要選取所有公開的虛擬方法，名為 「 MyMethod 」。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)

