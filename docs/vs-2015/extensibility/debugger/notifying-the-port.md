---
title: 通知連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81b27b4da563c01c809203690c05702530f58416
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47484928"
---
# <a name="notifying-the-port"></a>通知連接埠
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[通知連接埠](https://docs.microsoft.com/visualstudio/extensibility/debugger/notifying-the-port)。  
  
啟動程式之後, 的連接埠必須會收到通知，，如下所示：  
  
1.  當連接埠接收新的 [程式] 節點時，它會將程式建立事件送回偵錯工作階段中。 事件會有代表程式的介面。  
  
2.  偵錯工作階段會查詢的程式可以將附加至偵錯引擎 (DE) 的識別碼。  
  
3.  偵錯工作階段會檢查裝置允許 DEs，該程式的清單上。 偵錯工作階段會取得這份清單，從方案的使用中的程式設定中，原本由偵錯封裝，以傳遞給它。  
  
     裝置必須在允許清單中，否則 DE 將不會附加至程式。  
  
 以程式設計的方式，當連接埠先接收新的方案節點，它會建立[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)介面代表程式。  
  
> [!NOTE]
>  這不應該混淆與`IDebugProgram2`稍後由偵錯引擎 (DE) 的介面。  
  
 連接埠傳送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)程式建立事件回到工作階段偵錯管理員 (SDM) 透過 COM`IConnectionPoint`介面。  
  
> [!NOTE]
>  這不應該混淆與`IDebugProgramCreateEvent2`DE 稍後傳送的介面。  
  
 事件介面本身，以及傳送連接埠[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)， [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)，和[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)介面，代表此連接埠，處理，以及程式，分別。 SDM 呼叫[IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)取得可以偵錯程式 DE 的 GUID。 原本取自 GUID [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)介面。  
  
 SDM 會檢查裝置允許 DEs 清單上。 SDM 取得這份清單，從方案的使用中的程式設定中，原本由偵錯封裝，以傳遞給它。 裝置必須在允許清單中，否則將不會附加至程式。  
  
 一旦已知的裝置身分識別，就有一個 SDM 可將它附加至該程式。  
  
## <a name="see-also"></a>另請參閱  
 [啟動程式](../../extensibility/debugger/launching-a-program.md)   
 [在啟動後附加](../../extensibility/debugger/attaching-after-a-launch.md)   
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)

