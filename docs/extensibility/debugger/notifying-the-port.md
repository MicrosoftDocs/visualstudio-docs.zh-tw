---
title: "通知連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91bedf387fe86c2bf2fefb34e643e581a37c15bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="notifying-the-port"></a>通知連接埠
之後啟動程式，連接埠必須要收到通知，，如下所示：  
  
1.  當連接埠接收新的程式節點時，它會將傳回給偵錯工作階段的程式建立事件。 事件會夾帶表示程式的介面。  
  
2.  偵錯工作階段會查詢的程式可以將附加至偵錯引擎 (DE) 的識別碼。  
  
3.  偵錯工作階段會檢查以查看 DE 是否允許該程式 DEs 清單上。 偵錯工作階段中取得此清單從原本由偵錯封裝傳遞給它的解決方案中的程式設定。  
  
     DE 必須在允許清單中，否則 DE 將不會附加至程式。  
  
 以程式設計的方式，當連接埠先接收新的程式節點時，它會建立[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)介面代表程式。  
  
> [!NOTE]
>  這應該不與混淆`IDebugProgram2`稍後由偵錯引擎 (DE) 的介面。  
  
 連接埠傳送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)回到工作階段偵錯管理員 (SDM) 透過 COM 程式建立事件`IConnectionPoint`介面。  
  
> [!NOTE]
>  這應該不與混淆`IDebugProgramCreateEvent2`DE 稍後傳送的介面。  
  
 事件介面本身，以及連接埠傳送[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)， [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)，和[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)介面，表示連接埠，請處理，並程式，分別。 SDM 呼叫[IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)取得可以偵錯程式 DE 的 GUID。 原本取自 GUID [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)介面。  
  
 SDM 檢查 DE 是否允許 DEs 清單上。 SDM 從原本由偵錯封裝傳遞給它的解決方案中的程式設定中取得這份清單。 DE 必須在允許清單中，否則將不會附加至程式。  
  
 一旦 DE 身分識別已知時，就有一個 SDM 可將它附加至程式。  
  
## <a name="see-also"></a>另請參閱  
 [啟動程式](../../extensibility/debugger/launching-a-program.md)   
 [在啟動後附加](../../extensibility/debugger/attaching-after-a-launch.md)   
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)