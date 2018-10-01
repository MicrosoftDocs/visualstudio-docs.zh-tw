---
title: IDebugProgramNode2::DetachDebugger_V7 | Microsoft Docs
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
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bf8948873818185285c3285bb8b2dbdaf4aac256
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497926"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugProgramNode2::DetachDebugger_V7](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7)。  
  
已被取代。 請勿使用。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```csharp  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>傳回值  
 實作應該一律傳回`E_NOTIMPL`。  
  
## <a name="remarks"></a>備註  
  
> [!WARNING]
>  至於[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]，這個方法已不再使用，且應該一律傳回`E_NOTIMPL`。  
  
 偵錯工具意外結束時，會呼叫這個方法。 呼叫這個方法時，DE 應該繼續程式，如同使用者已從它中斷連結。 應該不傳送任何偵錯事件。 程式應該要在其所在之可附加的偵錯工具的另一個執行個體的狀態。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

