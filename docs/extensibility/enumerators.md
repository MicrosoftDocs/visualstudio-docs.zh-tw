---
title: 列舉值 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e57f11f61a1bcb2372a07e34167ecacd324067c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037784"
---
# <a name="enumerators"></a>列舉值
此區段會列出原始檔控制外掛程式必須了解原始檔控制外掛程式 API 中的列舉值資料類型。  
  
## <a name="in-this-section"></a>本節內容  
 [指令碼](../extensibility/command-code-enumerator.md)  
 列舉的選項[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)並[SccPopulateList](../extensibility/sccpopulatelist-function.md)函式。  
  
 [訊息](../extensibility/message-enumerator.md)  
 列舉列印的回呼，用旗標[LPTEXTOUTPROC](../extensibility/lptextoutproc.md)。  
  
 [檔案狀態碼](../extensibility/file-status-code-enumerator.md)  
 包含指定的原始檔控制下的檔案狀態的具名常數值。  
  
 [目錄狀態碼](../extensibility/directory-status-code-enumerator.md)  
 包含具名常數的值，指定狀態的原始檔控制之下的目錄。  
  
## <a name="related-sections"></a>相關章節  
 [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)  
 定義原始檔控制外掛程式 SDK，並說明內含的資源。  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 提示使用者提供指定的命令的進階選項。  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 會檢查其目前狀態的檔案清單。 此外，會使用`pfnPopulate`檔案類型不符合的準則時告知呼叫端函式`nCommand`。  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 描述回呼函式，以供[SccOpenProject](../extensibility/sccopenproject-function.md)顯示從原始檔控制外掛程式，透過 IDE 的訊息。  
  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)  
 提供原始檔控制外掛程式 API 中的所有項目的完整清單。