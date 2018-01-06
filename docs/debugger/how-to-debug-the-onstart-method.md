---
title: "如何： 偵錯 OnStart 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b482189ca4018cb3d55c2b35ecff3578863410a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-the-onstart-method"></a>如何：偵錯 OnStart 方法
您可以藉由啟動服務並將偵錯工具附加到服務處理序，對 Windows 服務進行偵錯。 如需詳細資訊，請參閱 [How to: Debug Windows Service Applications](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)。 但是若要對 Windows 服務的 <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> 方法進行偵錯，您必須從方法內啟動偵錯工具。  
  
1.  在 <xref:System.Diagnostics.Debugger.Launch%2A> 方法的開頭加入對 `OnStart()`的呼叫。  
  
    ```CSharp  
    protected override void OnStart(string[] args)  
    {  
        System.Diagnostics.Debugger.Launch();  
     }  
    ```  
  
2.  啟動服務 (您可以使用 `net start`，或在 [服務]  視窗中加以啟動)。  
  
     您應該會看到如下所示的對話方塊：  
  
     ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")  
  
3.  選取**[是]，偵錯\<服務名稱 >。**  
  
4.  在 [Just-In-Time 偵錯工具] 視窗中，選取您要用來偵錯的 Visual Studio 版本。  
  
     ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5.  Visual Studio 的新執行個體隨即啟動，並在 `Debugger.Launch()` 方法停止執行。  
  
## <a name="see-also"></a>請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)