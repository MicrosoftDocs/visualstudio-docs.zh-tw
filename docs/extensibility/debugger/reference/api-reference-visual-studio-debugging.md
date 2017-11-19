---
title: "API 參考 （Visual Studio 偵錯） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ead1571856fa04e10103fbf2274dc0e22295154
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="api-reference-visual-studio-debugging"></a>API 參考 （Visual Studio 偵錯）
參考章節包含的 api，顯示的語法和使用方式，針對所有應用程式開發介面項目，指南概念性概觀和程式碼範例的分類。 依類別目錄依字母順序列出所有參考。  
  
 下表顯示一般`HRESULT`方法所傳回的值。  
  
|名稱|描述|值|  
|----------|-----------------|-----------|  
|S_OK|成功。|0x00000000|  
|E_UNEXPECTED|未預期的失敗。|0x8000FFFF|  
|E_NOTIMPL|未實作。|0x80004001|  
|E_OUTOFMEMORY|記憶體不足，無法完成作業。|0x8007000E|  
|E_INVALIDARG|一或多個引數均為無效。|0x80070057|  
|E_NOINTERFACE|不支援這種介面。|0x80004002|  
|E_POINTER|無效的指標。|0x80004003|  
|E_HANDLE|無效的控制代碼。|0x80070006|  
|E_ABORT|作業已中止。|0x80004004|  
|E_FAIL|未預期的失敗。|0x80004005|  
|E_ACCESSDENIED|一般存取被拒的錯誤。|0x80070005|  
  
> [!NOTE]
>  當[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯方法會傳回`S_OK`，確認所有參數的指標有效，亦即，未驗證的進行上 out 參數的指標，它會都假設當`S_OK`傳回。  
  
> [!NOTE]
>  無效或`NULL`[out] 參數可能會造成損毀 IDE。  
  
## <a name="see-also"></a>另請參閱  
 [介面](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SDK 進行偵錯的協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Visual Studio 偵錯工具的擴充性](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)