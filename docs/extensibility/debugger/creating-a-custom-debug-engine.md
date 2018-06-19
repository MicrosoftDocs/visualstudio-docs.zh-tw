---
title: 建立自訂偵錯引擎 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 66ec73a13a3494ae6642e6d0f7397c9f3c1f0b0b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101374"
---
# <a name="creating-a-custom-debug-engine"></a>建立自訂的偵錯引擎
偵錯引擎 (DE) 是一種元件，可讓特定的執行階段架構的偵錯。 通常是只有一個 DE 實作每個執行階段環境。  
  
> [!NOTE]
>  TRANSACT-SQL 和 JScript 的個別 DE 實作時，VBScript 和 JScript 共用單一 DE。  
  
 DE 搭配直譯器或作業的系統，以提供執行控制項、 中斷點及運算式評估為這類偵錯服務。 這些服務透過 DE 介面實作，而且可能會造成偵錯工具不同的作業模式之間轉換。 如需詳細資訊，請參閱[作業模式](../../extensibility/debugger/operational-modes.md)。  
  
 建立 DE 包含下列步驟：  
  
1.  使用 Visual Studio 註冊 DE  
  
2.  啟用要進行偵錯的程式  
  
3.  執行控制項和狀態評估  
  
4.  傳送事件  
  
5.  終止並卸離  
  
## <a name="in-this-section"></a>本節內容  
 [註冊自訂的偵錯引擎](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 說明 Visual Studio 偵錯引擎註冊，使其可用於所需的步驟。  
  
 [啟用要偵錯的程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 說明您 DE 偵錯程式之前，您必須先啟動 DE 或將它附加至現有的程式。  
  
 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 討論偵錯應用程式為何需要實作執行控制功能。  
  
 [傳送事件](../../extensibility/debugger/sending-events.md)  
 描述偵錯工具與 DE 之間的通訊為 DCOM 所根據的事件模型。  
  
 [終止並中斷連結](../../extensibility/debugger/termination-and-detaching.md)  
 說明如何達成正常終止，這表示，沒有任何中斷點、 例外狀況，執行階段錯誤或要進行偵錯應用程式中的無限迴圈。  
  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)  
 文件偵錯工作階段中發生的事件的呼叫的順序。  
  
 [如何：偵錯自訂的偵錯引擎](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 說明如何偵錯自訂 DE。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 偵錯工具的擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)