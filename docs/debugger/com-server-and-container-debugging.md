---
title: COM 伺服器和容器偵錯 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- COM servers, debugging
- ActiveX controls, debugging
- COM [Visual Studio], debugging
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa27c3d63a21bf3a1cad31bb705df6532eed873c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="com-server-and-container-debugging"></a>COM 伺服器和容器偵錯
COM 應用程式可以在程式設計人員直接控制之外執行許多工作。 DLL 之間的通訊、物件的使用次數和剪貼簿作業只是您可能碰到預期外行為的一小部分而已。 發生這種狀況時，第一步驟便是追蹤搜尋問題的來源。  
  
 Visual Studio 偵錯工具可支援逐步跨越 (Step Across) 和逐步執行容器和伺服器。 這包括可支援逐步跨越遠端程序呼叫 (RPC)。  
  
##  <a name="BKMK_COMServerandContainerintheSameSolution"></a> 偵錯 COM 伺服器和相同方案中的容器  
 您可以同一方案內使用兩個專案的 COM 伺服器和容器 (Container) 進行偵錯。 在每個專案中設定適當的中斷點，並進行偵錯。 當容器在碰到中斷點的伺服器呼叫函式時，該容器將會等待，直到從伺服端程式碼傳回 (也就是直到您完成其偵錯程序)。  
  
 偵錯 COM 容器的方法和標準程式的偵錯方法相似。 不同之處在於您在偵錯一個會產生回呼 (Callback) 的事件時 (例如將資料拖曳到容器應用程式上)。 在這種情況下，您必須在回呼函式 (Callback Function) 中設定一中斷點。  
  
##  <a name="BKMK_ServerApplicationWithoutContainerInformation"></a> 偵錯伺服器應用程式沒有容器資訊  
 如果您沒有或不想使用容器應用程式的偵錯資訊，即可採用三步驟的處理方式，開始偵錯伺服器應用程式：  
  
1.  如應用程式方式開始偵錯伺服器。  
  
2.  依需要設定中斷點。  
  
3.  啟動容器應用程式 (Container Application)。  
  
##  <a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> 伺服器和網域隔離 (SDI) 應用程式進行偵錯  
 如果您正在偵錯 SDI 伺服器應用程式，您必須指定`/Embedding`或`/Automation`中**命令列引數**屬性*專案*屬性頁對話方塊中，C/c + +、 C# 中，或Visual Basic 專案。  
  
 透過這些命令列的引數，偵錯工具可以啟動伺服器應用程式，就如同它是由容器所啟動。 從程式管理員或檔案管理員啟動容器，將導致容器使用由偵錯工具啟動的伺服器執行個體。  
  
 若要存取*專案*屬性頁 對話方塊中，以滑鼠右鍵按一下方案總管 中的專案，並從捷徑功能表，然後選擇 屬性。 若要尋找 [命令列的引數] 屬性，請展開 [組態屬性] 分類，然後按一下 [偵錯] 頁。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 COM 和 ActiveX](../debugger/com-and-activex-debugging.md)