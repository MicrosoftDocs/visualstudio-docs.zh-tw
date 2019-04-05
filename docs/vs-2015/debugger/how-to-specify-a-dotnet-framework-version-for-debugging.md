---
title: HOW TO：指定偵錯.NET Framework 版本 |Microsoft Docs
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
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b3e5d7ebb1f61ffdbff98f49f83025115c80f64
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941229"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>HOW TO：指定偵錯.NET Framework 版本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 偵錯工具支援偵錯舊版 Microsoft [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 以及最新的版本。 如果您從 Visual Studio 啟動應用程式，則偵錯工具一律可以為正在偵錯的應用程式識別正確 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本。 如果已在執行應用程式，並使用**附加至**，偵錯工具不一定能夠識別舊版[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]。 如果發生這種情況，就會出現錯誤訊息：  
  
 偵錯工具對於應用程式所要使用的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本做了不正確的假設。  
  
 在這些不常見的情況中，您可以設定登錄機碼指示偵錯工具要使用的版本。  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>若要指定偵錯的 .NET Framework 版本  
  
1.  查詢目錄 Windows\Microsoft.NET\Framework 以尋找電腦上已安裝的 .NET Framework 版本。 版本號碼看起來如下所示：  
  
     `V1.1.4322`  
  
     識別正確的版本編號然後記下來。  
  
2.  啟動 [登錄編輯程式] (regedit)。  
  
3.  在 [登錄編輯程式] 中開啟 HKEY_LOCAL_MACHINE 資料夾。  
  
4.  瀏覽至：HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     如果此機碼不存在，請以滑鼠右鍵按一下 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine，然後按一下 [新增機碼]。 新的機碼命名`{449EC4CC-30D2-4032-9256-EE18EB41B62B}`。  
  
5.  在巡覽至 {449EC4CC-30D2-4032-9256-EE18EB41B62B} 後，查詢 [名稱] 欄位然後尋找 CLRVersionForDebugging 機碼。  
  
    1.  如果機碼不存在，請以滑鼠右鍵按一下 {449EC4CC-30D2-4032-9256-EE18EB41B62B}，然後按一下 [新增字串值]。 然後以滑鼠右鍵按一下新的字串值，請按一下**重新命名**，然後輸入`CLRVersionForDebugging`。  
  
6.  按兩下 [CLRVersionForDebugging]。  
  
7.  在 [編輯字串] 方塊的 [值] 方塊中鍵入 .NET Framework 版本號碼。 例如: V1.1.4322  
  
8.  按一下 [確定 **Deploying Office Solutions**]。  
  
9. 關閉 [登錄編輯程式]。  
  
     如果在開始偵錯時仍然出現錯誤訊息，請確認已經在登錄中正確輸入版本編號。 同時確認是使用 Visual Studio 支援的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本。 偵錯工具與 .NET Framework 的最新版本和舊版相容，但是不一定與未來的版本相容。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)
