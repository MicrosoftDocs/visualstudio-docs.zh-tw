---
title: "虛擬變數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: "35"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e2e5e716bd63170554537ec77895055de1fd83a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Visual Studio 偵錯工具中的虛擬變數
虛擬變數是用來顯示在變數視窗中的特定資訊的詞彙或**快速監看式** 對話方塊。 輸入虛擬變數的方式與輸入一般變數相同。 但虛擬變數並不是變數，而且不會對應至您程式中的變數名稱。  
  
## <a name="example"></a>範例  
 假設您在編寫機器碼應用程式，並且想要查看配置在應用程式中的控點數目。 在**監看式**視窗中，您可以輸入下列虛擬變數中的**名稱**資料行，然後按 Return 來進行評估：  
  
```  
$handles  
```  
  
 在機器碼中，您可以使用下表中顯示的虛擬變數：  
  
|虛擬變數|函式|  
|--------------------|--------------|  
|`$err`|顯示以 SetLastError 函式設定的最後錯誤值。 所顯示的值代表 GetLastError 函式會傳回的內容。<br /><br /> 請使用 `$err,hr` 來查看此值的解碼表單。 例如，如果最後錯誤是 3，則 `$err,hr` 會顯示 `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|顯示配置在您的應用程式中的控點數目。|  
|`$vframe`|顯示目前堆疊框架的位址。|  
|`$tid`|顯示目前執行緒的執行緒 ID。|  
|`$env`|顯示字串檢視器中的環境區塊。|  
|`$cmdline`|顯示啟動程式的命令列字串。|  
|`$pid`|顯示處理序 ID。|  
|`$`*registername*<br /><br /> 或<br /><br /> `@`*registername*|會顯示暫存器的內容*registername*。<br /><br /> 通常只要輸入註冊名稱，即可顯示註冊內容。 您唯一需要使用此語法的時機，就是當註冊名稱多載變數名稱時。 如果註冊名稱與目前範圍內的變數名稱相同，偵錯工具會將該名稱解譯為變數名稱。 這是當`$` *registername*或`@` *registername*派上用場。|  
|`$clk`|以時脈週期顯示時間。|  
|`$user`|針對執行應用程式的帳戶，顯示含有帳戶資訊的結構。 為安全起見，不會顯示密碼資訊。|  
|`$exceptionstack`|顯示目前 Windows 執行階段例外狀況的堆疊追蹤。 `$ exceptionstack`只有在 UWP 和 Windows 8.1 應用程式或更新版本的運作方式。 針對 C++ 和 SHE 例外狀況，不支援 `$ exceptionstack`。|  
|`$ReturnValue`|顯示 .NET Framework 方法的傳回值。|  
  
 在 C# 和 Visual Basic 中，您可以使用下表中顯示的虛擬變數：  
  
|虛擬變數|函式|  
|--------------------|--------------|  
|`$exception`|顯示最後例外狀況的資訊。 如果沒有發生例外狀況，評估 `$exception` 會顯示錯誤訊息。<br /><br /> Visual C# 中，例外狀況助理停用時，`$exception`會自動加入至**區域變數**視窗時發生例外狀況。|  
|`$user`|針對執行應用程式的帳戶，顯示含有帳戶資訊的結構。 為安全起見，不會顯示密碼資訊。|  
  
 在 Visual Basic 中，您可以使用下表中顯示的虛擬變數：  
  
|虛擬變數|功能|  
|--------------------|--------------|  
|`$delete` 或 `$$delete`|刪除所建立的隱含變數**即時運算**視窗。 語法是`$delete,`*變數*或`$delete,`*變數*`.`|  
|`$objectids` 或 `$listobjectids`|將所有作用中物件 ID 顯示為指定運算式的子項。 語法是`$objectid,`*運算式*或`$listobjectids,`*運算式*`.`|  
|`$`*N*`#`|顯示物件具有相等的物件識別碼*N*。|  
|`$dynamic`|顯示特殊**動態檢視**實作物件節點`IDynamicMetaObjectProvider`。 介面。 語法是`$dynamic,`*物件*。 此功能僅適用於使用 .NET Framework 第 4 版的程式碼。|  
  
## <a name="see-also"></a>請參閱  
 [監看式和快速監看式視窗](../debugger/watch-and-quickwatch-windows.md)   
 [變數視窗](../debugger/debugger-windows.md)