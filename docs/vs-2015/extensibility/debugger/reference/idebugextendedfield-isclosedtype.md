---
title: IDebugExtendedField::IsClosedType |Microsoft Docs
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
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 82330c1d6ea06b8eea6b69bf590e2baba4213fcf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825279"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

決定是否表示封閉式的型別欄位。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT IsClosedType(  
   void  
);  
```  
  
```csharp  
int IsClosedType();  
```  
  
## <a name="return-value"></a>傳回值  
 如果欄位是封閉式的型別，會傳回`S_OK`; 否則傳回`S_FALSE`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)

