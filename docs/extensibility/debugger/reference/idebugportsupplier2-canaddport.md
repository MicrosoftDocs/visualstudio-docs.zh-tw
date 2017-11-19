---
title: "IDebugPortSupplier2::CanAddPort |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier2::CanAddPort
helpviewer_keywords: IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6f19d220f8638b84e194ab1604816ed767d10c41
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
確認連接埠供應商可以新增新的連接埠。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CanAddPort(   
   void   
);  
```  
  
```csharp  
int CanAddPort();  
```  
  
## <a name="return-value"></a>傳回值  
 如果可以加入連接埠，會傳回`S_OK`; 否則傳回`S_FALSE`表示沒有連接埠可以加入到此連接埠供應商。  
  
## <a name="remarks"></a>備註  
 呼叫這個方法之前先呼叫[下列](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)方法，因為第二個方法會建立連接埠，以及加入它，可能耗時的作業。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [下列](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)