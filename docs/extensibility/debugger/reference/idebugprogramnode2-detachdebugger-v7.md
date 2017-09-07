---
title: "IDebugProgramNode2::DetachDebugger_V7 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: a281d92d93473dffeb8f488cd802a9cee4a779d7
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
已被取代。 請勿使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```csharp  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>傳回值  
 實作應該會一律傳回`E_NOTIMPL`。  
  
## <a name="remarks"></a>備註  
  
> [!WARNING]
>  從[!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]，此方法已不再使用，而且應該會一律傳回`E_NOTIMPL`。  
  
 偵錯工具意外結束時，會呼叫這個方法。 呼叫這個方法時，DE 應該繼續程式，如同使用者中斷。 應該不傳送任何偵錯事件。 程式應該是可附加的偵錯工具的另一個執行個體的狀態中。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
