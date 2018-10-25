---
title: IDebugCoreServer3::QueryIsLocal |Microsoft Docs
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
- IDebugCoreServer3::QueryIsLocal
helpviewer_keywords:
- IDebugCoreServer3::QueryIsLocal
ms.assetid: cca030de-f853-4ed7-b2fb-395f08a6b884
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9bd8b13748f42aff635579899555fffce72d51ec
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949093"
---
# <a name="idebugcoreserver3queryislocal"></a>IDebugCoreServer3::QueryIsLocal
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

判斷伺服器是否為本機呼叫端。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT QueryIsLocal(  
   void  
);  
```  
  
```csharp  
int QueryIsLocal();  
```  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`表示本機伺服器。 傳回`S_FALSE`如果伺服器正在執行 msvsmon.exe，通常用於遠端偵錯執行個體中。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)

