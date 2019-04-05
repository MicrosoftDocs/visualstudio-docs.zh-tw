---
title: 安全性問題 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 874231333c87020c126eac4c066d53512ba0bbc9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58929986"
---
# <a name="security-issues"></a>安全性問題
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

若要偵錯使用 Visual Studio 的程式，所需的權限僅限於都相同的開發人員必須執行的程式。 這包括大部分的情況下 （牽涉到其他服務，例如網際網路資訊服務，某些情況下可能需要較高層級的權限） 的遠端偵錯。  
  
 當 Visual Studio 執行時，處理序偵錯管理員 (PDM) 會在本機電腦上追蹤偵錯處理序。 遠端電腦上，開發人員來處理遠端偵錯，並提供 PDM 所啟動程式，稱為 msvsmon.exe。 （請注意 msvsmon.exe 並不是服務，而且必須以手動方式啟動，才能啟用該電腦上的遠端偵錯）。當 Visual Studio （或 msvsmon.exe） 未執行時，會追蹤沒有任何處理序偵錯。  
  
 這表示開發人員可以偵錯的程式他或她開始使用任何特殊權限。 開發人員甚至可以偵錯處理序啟動由其他人，對方是否相同的安全性群組的成員。 若要啟用遠端偵錯，就必須只複製所需之檔案至遠端電腦並開始 msvsmon.exe 和 (請參閱[設定 Up the Remote Tools 在裝置上](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)如需詳細資訊)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)   
 [處理序偵錯管理員](../../extensibility/debugger/process-debug-manager.md)   
 [在裝置上設定遠端工具](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
