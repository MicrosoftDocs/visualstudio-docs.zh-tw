---
title: 列舉值 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84102435092096b7154a46100e9d857a31537482
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="enumerators"></a>列舉值
此區段會列出原始檔控制外掛程式必須知道原始檔控制外掛程式 API 中的列舉值資料型別。  
  
## <a name="in-this-section"></a>本節內容  
 [指令碼](../extensibility/command-code-enumerator.md)  
 列舉的選項[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)和[SccPopulateList](../extensibility/sccpopulatelist-function.md)函式。  
  
 [Message](../extensibility/message-enumerator.md)  
 列舉旗標用於列印的回呼， [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)。  
  
 [檔案狀態碼](../extensibility/file-status-code-enumerator.md)  
 包含具名常數的值，指定在原始檔控制檔案的狀態。  
  
 [目錄的狀態碼](../extensibility/directory-status-code-enumerator.md)  
 包含具名常數的值，指定狀態的原始檔控制下的目錄。  
  
## <a name="related-sections"></a>相關章節  
 [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)  
 定義原始檔控制外掛程式 SDK，並描述包含的資源。  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 提示使用者提供對於指定的命令的進階選項。  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 會檢查其目前狀態的檔案清單。 此外，使用`pfnPopulate`函式的檔案不相符的準則時，通知呼叫端`nCommand`。  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 描述回呼函式，以供[SccOpenProject](../extensibility/sccopenproject-function.md)顯示從原始檔控制外掛程式透過 IDE 的訊息。  
  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)  
 提供完整的原始檔控制外掛程式 API 中的所有項目清單。