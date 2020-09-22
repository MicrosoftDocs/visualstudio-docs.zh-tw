---
title: 如何：啟動 Spy + + |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 36555d9b00c9aff3f594ae2217afe8434bb41542
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839129"
---
# <a name="how-to-start-spy"></a>如何：啟動 Spy++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以從 Visual Studio 或命令提示字元啟動 Spy + +。  
  
 當您啟動 Spy + + 時，如果顯示訊息以要求對電腦進行變更的許可權，請按一下 **[是]**。  
  
> [!NOTE]
> 您只能執行一個 Spy + + 實例。 如果您嘗試執行另一個實例，則只會導致目前正在執行的實例取得焦點。  
  
### <a name="to-start-spy-from-visual-studio"></a>從 Visual Studio 啟動 Spy + +  
  
- 按一下 [ **工具** ] 功能表上的 [ **Spy + +**]。  
  
     因為 Spy + + 會獨立執行，所以在您啟動它之後，就可以關閉 Visual Studio。  
  
    > [!NOTE]
    > 當您使用 Spy + + 記錄訊息時，可能會導致作業系統執行得更慢。  
  
### <a name="to-start-spy-at-a-command-prompt"></a>若要在命令提示字元中啟動 Spy + +  
  
1. 在 [命令提示字元] 視窗中，將目錄變更為包含 spyxx.exe 的資料夾。 一般而言，此資料夾的路徑為。 \\*Visual Studio 安裝資料夾*\Common7\Tools \\ 。  
  
2. 輸入 **spyxx.exe** ，然後按 enter。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Spy + +](../debugger/using-spy-increment.md)   
 [Spy + + Views](../debugger/spy-increment-views.md)   
 [Spy++ 參考](../debugger/spy-increment-reference.md)
