---
title: 如何： 啟動 Spy + + |Microsoft Docs
ms.custom: ''
ms.date: 11/12/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e2e5ffabbb560165bd19bb3d52b940a5cc9e858
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257157"
---
# <a name="how-to-start-spy"></a>如何：啟動 Spy++
您可以啟動 Spy + + 從 Visual Studio 或命令提示字元。  
  
 當您啟動 Spy + + 中，如果會顯示訊息要求權限來變更電腦，請選取**是**。  
  
> [!NOTE]
>  您可以執行 Spy + + 的只有一個執行的個體。 如果您嘗試啟動第二個執行個體，它只會導致目前正在執行的執行個體，以取得焦點。  
  
### <a name="start-spy-from-visual-studio"></a>從 Visual Studio 啟動 Spy + +  
  
在 **工具**功能表上，選取**Spy + +**。  
  
因為 Spy + + 會獨立執行，您在開始之後，您可以關閉 Visual Studio。  
  
> [!NOTE]
>  當您使用 Spy + + 記錄訊息時，它可能會造成作業系統執行速度變慢。  
  
### <a name="start-spy-at-a-command-prompt"></a>在命令提示字元啟動 Spy + +  
  
1.  在命令提示字元視窗中，將目錄變更為包含 spyxx.exe 的資料夾。 一般而言，此資料夾的路徑是...\\ *Visual Studio 安裝資料夾*\Common7\Tools\\。  
  
2.  請輸入**spyxx.exe**。 
  
## <a name="see-also"></a>另請參閱  
 [使用 Spy + +](../debugger/using-spy-increment.md)   
 [Spy + + 檢視](../debugger/spy-increment-views.md)   
 [Spy++ 參考](../debugger/spy-increment-reference.md)