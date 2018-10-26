---
title: IDebugDocumentTextEvents2::onUpdateDocumentAttributes |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentTextEvents2::OnUpdateDocumentAttributes
helpviewer_keywords:
- IDebugDocumentTextEvents2::onUpdateDocumentAttributes
ms.assetid: 31b7d151-9ce2-438e-b405-f8cc46b9f537
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5cb76fc0d90dfd76fbf45e629f03b59052fda05a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883070"
---
# <a name="idebugdocumenttextevents2onupdatedocumentattributes"></a>IDebugDocumentTextEvents2::onUpdateDocumentAttributes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

通知事件的接收者，已更新的文件屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT onUpdateDocumentAttributes(   
   TEXT_DOC_ATTR_2 textdocattr  
);  
```  
  
```csharp  
int onUpdateDocumentAttributes(   
   enum_TEXT_DOC_ATTR_2 textdocattr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `textdocattr`  
 [in]從旗標的組合[TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md)列舉，指定的文件更新的屬性。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md)

