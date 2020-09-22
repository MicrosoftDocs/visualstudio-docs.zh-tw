---
title: IDebugProgramNode2：:D etachDebugger_V7 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c60bc42895a0527f1638dada5a28a1631314e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838988"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

廢棄。 請勿使用。  
  
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
 實作為應一律傳回 `E_NOTIMPL` 。  
  
## <a name="remarks"></a>備註  
  
> [!WARNING]
> 從 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 之後，這個方法已不再使用，應該一律傳回 `E_NOTIMPL` 。  
  
 當偵錯工具意外結束時，會呼叫這個方法。 當呼叫這個方法時，DE 應該會繼續執行程式，就好像使用者卸離它一樣。 不應傳送更多的 debug 事件。 程式應處於可從偵錯工具的另一個實例附加的狀態。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
