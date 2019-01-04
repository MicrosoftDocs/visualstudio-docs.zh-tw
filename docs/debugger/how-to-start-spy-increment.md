---
title: HOW TO：啟動 Spy + + |Microsoft Docs
ms.custom: ''
ms.date: 12/16/2018
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
ms.openlocfilehash: 5143c34f0c344fecec82a5d08b2e7fb9b95ac1bc
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646863"
---
# <a name="how-to-start-spy"></a>HOW TO：啟動 Spy++

您可以啟動 Spy + + 從 Visual Studio 或命令提示字元。  
  
 當您啟動 Spy + + 中，如果會顯示訊息要求權限來變更電腦，請選取**是**。  
  
> [!NOTE]
>  您可以執行 Spy + + 的只有一個執行的個體。 如果您嘗試啟動第二個執行個體，它只會導致目前正在執行的執行個體，以取得焦點。

## <a name="prerequisites"></a>必要條件

Spy + + 需要下列元件。 您可以從 Visual Studio 安裝程式選取這些元件，方法是選取**個別元件**索引標籤，然後選取 下列元件。

* 在 偵錯和測試時，選取**c + + 程式碼剖析工具**
* 在 [開發活動] 下選取**Visual Studio c + + 核心功能**

如果您進行任何變更，請依照下列提示來安裝這些元件。
  
## <a name="start-spy-from-visual-studio"></a>從 Visual Studio 啟動 Spy + +
  
在 **工具**功能表上，選取**Spy + +**。  
  
因為 Spy + + 會獨立執行，您在開始之後，您可以關閉 Visual Studio。  
  
> [!NOTE]
>  當您使用 Spy + + 記錄訊息時，它可能會造成作業系統執行速度變慢。  
  
## <a name="start-spy-at-a-command-prompt"></a>在命令提示字元啟動 Spy + +  
  
1.  在命令提示字元視窗中，將目錄變更為包含 spyxx.exe 的資料夾。 一般而言，此資料夾的路徑是...\\ *Visual Studio 安裝資料夾*\Common7\Tools\\。  
  
2.  請輸入**spyxx.exe**。 
  
## <a name="see-also"></a>另請參閱  
 [使用 Spy++](../debugger/using-spy-increment.md)   
 [Spy++ 檢視](../debugger/spy-increment-views.md)   
 [Spy++ 參考](../debugger/spy-increment-reference.md)