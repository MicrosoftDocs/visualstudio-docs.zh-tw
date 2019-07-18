---
title: IDebugDocumentTextEvents2::onUpdateTextAttributes |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnUpdateTextAttributes
helpviewer_keywords:
- IDebugDocumentTextEvents2::onUpdateTextAttributes
ms.assetid: eb68d69a-1ad9-4ce4-84e1-40979ef16634
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6eaa39ae3116a452488e80bf54c06ab4bde5cb64
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148733"
---
# <a name="idebugdocumenttextevents2onupdatetextattributes"></a>IDebugDocumentTextEvents2::onUpdateTextAttributes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

文件中，已更新文字屬性會告知偵錯封裝。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT onUpdateTextAttributes(   
   TEXT_POSITION pos,  
   DWORD         dwNumToUpdate  
);  
```  
  
```csharp  
int onUpdateTextAttributes(   
   enum_TEXT_POSITION pos,  
   uint               dwNumToUpdate  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pos`  
 [in]A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構，表示文字屬性已更新的位置。  
  
 `dwNumToUpdate`  
 [in]指定文字的已更新的字元數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
