---
title: IEnumDebugPorts2::Reset |Microsoft Docs
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
- IEnumDebugPorts2::Reset
helpviewer_keywords:
- IEnumDebugPorts2::Reset
ms.assetid: 67da406c-eadb-421e-ae12-e26e9866f262
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85e7083e9186352b1c6e1a601311334a3052edc3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47484827"
---
# <a name="ienumdebugports2reset"></a>IEnumDebugPorts2::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IEnumDebugPorts2::Reset](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugports2-reset)。  
  
將列舉重設第一個項目。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 呼叫這個方法是，下一個呼叫之後[下一步](../../../extensibility/debugger/reference/ienumdebugports2-next.md)方法會傳回第一個元素的列舉型別。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)

