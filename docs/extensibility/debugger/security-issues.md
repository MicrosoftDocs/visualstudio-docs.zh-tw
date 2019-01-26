---
title: 安全性問題 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4dcd9806459a1cdc92d3eb698fcae7b4a7e0fa6f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55016449"
---
# <a name="security-issues"></a>安全性問題
若要偵錯使用 Visual Studio 的程式，所需的權限僅限於都相同的開發人員需要用來執行程式。 這包括大多數的情況下執行遠端偵錯。 某些情況下，包含其他服務，例如網際網路資訊服務，可能需要較高層級的權限。  
  
 當 Visual Studio 執行時，處理序偵錯管理員 (PDM) 會在本機電腦上追蹤偵錯處理序。 遠端電腦上，稱為 「 計劃*msvsmon.exe*由開發人員處理遠端偵錯，並提供 PDM 啟動。 (*msvsmon.exe*不是服務，而且必須以手動方式啟動，才能啟用該電腦上的遠端偵錯。)當 Visual Studio (或*msvsmon.exe*) 是未執行，沒有任何處理序會追蹤偵錯。  
  
 開發人員可以偵錯他們開始任何特殊權限的程式。 開發人員甚至可以偵錯處理序啟動由其他人，對方是否相同的安全性群組的成員。 若要啟用遠端偵錯，則只需要將所需的檔案複製到遠端電腦，並啟動*msvsmon.exe*。 如需詳細資訊，請參閱 <c0> [ 遠端偵錯](../../debugger/remote-debugging.md)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)   
 [處理序偵錯管理員](../../extensibility/debugger/process-debug-manager.md)   
 [遠端偵錯](../../debugger/remote-debugging.md)
