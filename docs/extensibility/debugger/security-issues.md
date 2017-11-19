---
title: "安全性問題 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8061c419f81493e56a58df8fefbe4d3362d43e46
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="security-issues"></a>安全性問題
偵錯使用 Visual Studio 的程式，所需的唯一權限是相同的開發人員必須在執行程式。 這包括大部分的情況下 （與其他服務，例如網際網路資訊服務，某些情況下可能需要較高的層級的權限） 的遠端偵錯。  
  
 在 Visual Studio 執行時，處理序偵錯管理員 (PDM) 會追蹤偵錯處理序在本機電腦上。 遠端電腦上，msvsmon.exe 程式已啟動遠端偵錯的處理，並將 PDM 提供開發人員。 （請注意該 msvsmon.exe 不是服務，而且必須以手動方式啟動，才能啟用該電腦上的遠端偵錯）。當 Visual Studio （或 msvsmon.exe） 無法執行時，沒有任何處理序會追蹤偵錯。  
  
 這表示開發人員可以偵錯的程式他或她入門任何特殊權限。 開發人員甚至可以偵錯的其他人是否相同的安全性群組的成員，其他人來啟動處理序。 若要啟用遠端偵錯，就必須只將必要的複製檔案至遠端電腦並啟動 msvsmon.exe，(請參閱[遠端偵錯](../../debugger/remote-debugging.md)如需詳細資訊)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)   
 [處理序偵錯管理員](../../extensibility/debugger/process-debug-manager.md)   
 [遠端偵錯](../../debugger/remote-debugging.md)