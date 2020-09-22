---
title: API 參考 (Visual Studio 調試) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f3e95200cf29c8561798c858635c3864d635fb40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838890"
---
# <a name="api-reference-visual-studio-debugging"></a>API 參考 (Visual Studio 偵錯)
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

參考章節包含 API 的概念總覽，此指南會顯示所有 API 專案的語法和使用方式，以及各種程式碼範例。 所有參考都會依類別目錄依字母順序列出。  
  
 下表顯示方法所傳回的一般 `HRESULT` 值。  
  
|名稱|描述|值|  
|----------|-----------------|-----------|  
|S_OK|成功。|0x00000000|  
|E_UNEXPECTED|發生非預期的失敗。|0x8000FFFF|  
|E_NOTIMPL|未實作。|0x80004001|  
|E_OUTOFMEMORY|記憶體不足，無法完成操作。|0x8007000E|  
|E_INVALIDARG|一或多個引數無效。|0x80070057|  
|E_NOINTERFACE|不支援這類介面。|0x80004002|  
|E_POINTER|指標無效。|且顯示0x80004003|  
|E_HANDLE|控制碼無效。|0x80070006|  
|E_ABORT|作業已中止。|0x80004004|  
|E_FAIL|發生非預期的失敗。|0x80004005|  
|E_ACCESSDENIED|一般拒絕存取錯誤。|0x80070005|  
  
> [!NOTE]
> 當 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 偵錯工具傳回時 `S_OK` ，假設所有 out 參數指標都有效，也就是，當傳回時，不會對 out 參數指標進行驗證 `S_OK` 。  
  
> [!NOTE]
> 無效或 `NULL` [out] 參數可能導致 IDE 損毀。  
  
## <a name="see-also"></a>另請參閱  
 [介面](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [枚舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [用於偵錯工具的 SDK 協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Visual Studio 偵錯工具的擴充性](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
