---
title: "IDebugMethodField::EnumLocals |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField::EnumLocals
helpviewer_keywords: IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 451c2ccad7d817946bd3d2c2e83ed27279124f2b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
建立選取的本機變數之方法的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pAddress`  
 [in][IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件，表示選取的內容或範圍，從中取得區域變數的偵錯位址。  
  
 `ppLocals`  
 [out]傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件表示的區域變數清單; 如果沒有任何區域變數，反之則傳回 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功的話，會傳回 S_OK，或如果沒有任何區域變數闇 S_FALSE。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 列舉只能定義在包含指定的偵錯位址區塊內的變數。 如需所有區域變數，包括任何編譯器產生的區域變數，呼叫[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)方法。  
  
 一種方法可以包含多個範圍的內容或區塊。 例如，下列方法包含三個範圍、 兩個內部區塊和本身的方法主體。  
  
```csharp  
public void func(int index)  
{  
    // Method body scope  
    int a = 0;  
    if (index == 1)  
    {  
        // Inner scope 1  
        int temp1 = a;  
    }  
    else  
    {  
        // Inner scope 2  
        int temp2 = a;  
    }  
}  
```  
  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)物件代表`func`方法本身。 呼叫`EnumLocals`方法[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)設`Inner Scope 1`位址可讓您傳回列舉包含`temp1`變數，例如。  
  
## <a name="see-also"></a>請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)