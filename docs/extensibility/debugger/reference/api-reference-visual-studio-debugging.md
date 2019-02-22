---
title: API 參考 （Visual Studio 偵錯） |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8dfe0405406405dc1e09e18c49f7de7b4aecd7fa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013323"
---
# <a name="api-reference-visual-studio-debugging"></a>API 參考 (Visual Studio 偵錯)
參考章節包含的 API，顯示的語法和所有的 API 元素的使用方式指南的概念性概觀和各種程式碼範例。 所有參考會依分類依字母順序都列出。  
  
 下表顯示常見`HRESULT`方法所傳回的值。  
  
|名稱|描述|值|  
|----------|-----------------|-----------|  
|S_OK|成功。|0x00000000|  
|E_UNEXPECTED|未預期的失敗。|0x8000FFFF|  
|E_NOTIMPL|未實作。|0x80004001|  
|E_OUTOFMEMORY|記憶體不足，無法完成作業。|0x8007000E|  
|E_INVALIDARG|一或多個引數均為無效。|0x80070057|  
|E_NOINTERFACE|不支援此種介面。|0x80004002|  
|E_POINTER|無效的指標。|0x80004003|  
|E_HANDLE|無效的控制代碼。|0x80070006|  
|E_ABORT|作業已中止。|0x80004004|  
|E_FAIL|未預期的失敗。|0x80004005|  
|E_ACCESSDENIED|一般拒絕存取錯誤。|0x80070005|  
  
> [!NOTE]
>  當[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯方法會傳回`S_OK`，則會假設所有參數的指標都有效，也就是沒有驗證場地進行 out 參數的指標時`S_OK`會傳回。  
> 
> [!NOTE]
>  無效或`NULL`[out] 參數可能會造成 IDE 損毀。  
  
## <a name="see-also"></a>另請參閱  
 [介面](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [偵錯的 SDK 協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Visual Studio 偵錯工具的擴充性](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)