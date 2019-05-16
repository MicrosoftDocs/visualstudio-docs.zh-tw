---
title: 虛擬變數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9ce72d69cb64b0421771324803a785546fa884f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65693758"
---
# <a name="pseudovariables"></a>虛擬變數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

虛擬變數是在變數視窗或 [快速監看式] 對話方塊中，用來顯示特定資訊的詞彙。 輸入虛擬變數的方式與輸入一般變數相同。 但虛擬變數並不是變數，而且不會對應至您程式中的變數名稱。  
  
## <a name="example"></a>範例  
 假設您在編寫機器碼應用程式，並且想要查看配置在應用程式中的控點數目。 您可以在 [監看式] 視窗的 [名稱] 欄中，輸入下列虛擬變數，然後按 [傳回] 來進行評估：  
  
```  
$handles  
```  
  
 在機器碼中，您可以使用下表中顯示的虛擬變數：  
  
|虛擬變數|功能|  
|--------------------|--------------|  
|`$err`|顯示以 SetLastError 函式設定的最後錯誤值。 所顯示的值代表 GetLastError 函式會傳回的內容。<br /><br /> 請使用 `$err,hr` 來查看此值的解碼表單。 例如，如果最後錯誤是 3，則 `$err,hr` 會顯示 `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|顯示配置在您的應用程式中的控點數目。|  
|`$vframe`|顯示目前堆疊框架的位址。|  
|`$tid`|顯示目前執行緒的執行緒 ID。|  
|`$env`|顯示字串檢視器中的環境區塊。|  
|`$cmdline`|顯示啟動程式的命令列字串。|  
|`$pid`|顯示處理序 ID。|  
|`$` *registername*<br /><br /> 或<br /><br /> `@` *registername*|顯示註冊 *registername* 的內容。<br /><br /> 通常只要輸入註冊名稱，即可顯示註冊內容。 您唯一需要使用此語法的時機，就是當註冊名稱多載變數名稱時。 如果註冊名稱與目前範圍內的變數名稱相同，偵錯工具會將該名稱解譯為變數名稱。 這就是 `$`*registername* 或 `@`*registername* 派上用場的時候。|  
|`$clk`|以時脈週期顯示時間。|  
|`$user`|針對執行應用程式的帳戶，顯示含有帳戶資訊的結構。 為安全起見，不會顯示密碼資訊。|  
|`$exceptionstack`|顯示目前 Windows 執行階段例外狀況的堆疊追蹤。 `$ exceptionstack` 僅適用於在 Windows 8.1 或較新版本上執行的市集應用程式。 針對 C++ 和 SHE 例外狀況，不支援 `$ exceptionstack`。|  
|`$ReturnValue`|顯示 .NET Framework 方法的傳回值。 請參閱[檢查的方法呼叫的傳回值](https://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f)|  
  
 在 C# 和 Visual Basic 中，您可以使用下表中顯示的虛擬變數：  
  
|虛擬變數|功能|  
|--------------------|--------------|  
|`$exception`|顯示最後例外狀況的資訊。 如果沒有發生例外狀況，評估 `$exception` 會顯示錯誤訊息。<br /><br /> 僅限在 Visual C# 中，如果停用例外狀況助理，發生例外狀況時，會自動將 `$exception` 新增至 [本機] 視窗。|  
|`$user`|針對執行應用程式的帳戶，顯示含有帳戶資訊的結構。 為安全起見，不會顯示密碼資訊。|  
  
 在 Visual Basic 中，您可以使用下表中顯示的虛擬變數：  
  
|虛擬變數|功能|  
|--------------------|--------------|  
|`$delete` 或 `$$delete`|刪除在 [立即] 視窗中建立的隱含變數。 語法是`$delete,`*變數*或是`$delete,`*變數*`.`|  
|`$objectids` 或 `$listobjectids`|將所有作用中物件 ID 顯示為指定運算式的子項。 語法是`$objectid,`*運算式*或是`$listobjectids,`*運算式*`.`|  
|`$` *N* `#`|顯示物件識別碼等於 *N* 的物件。|  
|`$dynamic`|針對實作 `IDynamicMetaObjectProvider` 的物件，顯示特殊 [動態檢視] 節點。 介面。 語法為 `$dynamic,` *object*。 此功能僅適用於使用 .NET Framework 第 4 版的程式碼。 請參閱[動態檢視](https://msdn.microsoft.com/library/4c851b17-2c12-46a0-9828-eb6ea6f5c563)。|  
  
## <a name="see-also"></a>另請參閱  
 [監看式及快速監看式視窗](../debugger/watch-and-quickwatch-windows.md)   
 [變數視窗](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)
