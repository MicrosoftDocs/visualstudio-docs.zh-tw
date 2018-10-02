---
title: IDebugClassField::EnumInterfacesImplemented |Microsoft Docs
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
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9c21a20fc832a42baa7386f50289d8297a3e34f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491199"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugClassField::EnumInterfacesImplemented](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented)。  
  
建立這個類別所實作之介面的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT EnumInterfacesImplemented(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumInterfacesImplemented(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppEnum`  
 [out]傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，代表實作的介面清單。 如果沒有介面，則傳回 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK，或如果沒有在這個類別上實作介面，則傳回 S_FALSE。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 列舉型別的每個項目是[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)描述介面的物件。 請注意，非受控[!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)]程式碼不會使用介面當做離散實體讓這個方法永遠都會傳回 null 值的非受控[!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)]程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)

