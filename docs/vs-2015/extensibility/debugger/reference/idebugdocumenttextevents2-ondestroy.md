---
title: IDebugDocumentTextEvents2::onDestroy |Microsoft Docs
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
- IDebugDocumentTextEvents2::OnDestroy
helpviewer_keywords:
- IDebugDocumentTextEvents2::onDestroy
ms.assetid: 60e4689c-c899-4c14-9d18-96393b741e1f
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76b3764e3a20183d8372856bbf701450ac4c5367
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843661"
---
# <a name="idebugdocumenttextevents2ondestroy"></a>IDebugDocumentTextEvents2::onDestroy
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

表示已終結整份文件。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT onDestroy(   
   void   
);  
```  
  
```csharp  
int onDestroy();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)

