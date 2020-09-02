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
ms.openlocfilehash: fb6209882a7a71a68728299064edcc13afabff35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704416"
---
# <a name="security-issues"></a>安全性問題
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

若要使用 Visual Studio 來對程式進行偵錯工具，唯一需要的許可權，與開發人員執行程式所需的許可權相同。 這包括在大部分情況下進行遠端偵錯 (某些涉及其他服務的情況（例如網際網路資訊服務）可能需要較高層級的許可權) 。  
  
 當 Visual Studio 正在執行時，進程 debug manager (PDM) 會追蹤本機電腦上的偵錯工具。 從遠端開始，開發人員會啟動稱為 msvsmon.exe 的程式來處理遠端偵錯程式，並讓 PDM 可用。  (請注意，msvsmon.exe 不是服務，必須以手動方式啟動，才能在該電腦上啟用遠端偵錯程式。當 Visual Studio (或 msvsmon.exe) 未執行時，) 不會追蹤處理常式。  
  
 這表示開發人員可以在不使用任何特殊許可權的情況下，對其啟動的程式進行偵錯工具。 如果其他人是相同安全性群組的成員，開發人員甚至可以對其他人啟動的進程進行偵錯工具。 若要啟用遠端偵錯程式，只需要將必要的檔案複製到遠端電腦，然後啟動 msvsmon.exe (請參閱 [在裝置上設定遠端工具](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) ，以取得更多詳細資料) 。  
  
## <a name="see-also"></a>另請參閱  
 [調試作業](../../extensibility/debugger/debugging-tasks.md)   
 [進程偵錯工具管理員](../../extensibility/debugger/process-debug-manager.md)   
 [在裝置上設定遠端工具](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
