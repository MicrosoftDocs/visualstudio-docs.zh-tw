---
title: 遠端偵錯程式埠指派 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2628d8929a0d2b6fd3561f88c81cfaa3b62564f0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542099"
---
# <a name="remote-debugger-port-assignments"></a>遠端偵錯工具連接埠指派
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 遠端偵錯工具可以應用程式或背景服務的形式執行。 當以應用程式的形式執行時，它會使用預設指派的連接埠，如下所示：  
  
- Visual Studio 2015：4020  
  
- Visual Studio 2013：4018  
  
- Visual Studio 2012：4016  
  
  換句話說，指派給遠端偵錯工具的連接埠號碼會隨著每個版本遞增 2。 您可以設定您要的不同連接埠號碼。 我們將在稍後的章節中說明如何設定連接埠號碼。  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>32 位元作業系統上的遠端偵錯工具連接埠  
 (在 Visual Studio 2015 中) TCP 4020 是主要的連接埠，在所有情況下都需要。 您可以從命令列或遠端偵錯工具視窗來進行此設定。  
  
 在 [遠端偵錯程式] 視窗中，按一下 [**工具]/[選項**]，然後設定 tcp/ip 通訊埠編號。  
  
 在命令列上，使用 **/port**參數啟動遠端偵錯程式： **msvsmon/port \<port number> **。  
  
 您可以在 [遠端偵錯程式] 說明中找到所有遠端偵錯程式命令列參數（按**F1**或按一下 [遠端偵錯程式] 視窗中的 [說明] **/[使用**方式]）。  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>64 位元作業系統上的遠端偵錯工具連接埠  
 當啟動 64 位元版本的遠端偵錯工具時，它預設會使用 4020 連接埠。  如果您偵錯 32 位元處理序，64 位元版本的遠端偵錯工具會在連接埠 4021 啟動遠端偵錯工具的 32 位元版本。 如果您執行 32 位元遠端偵錯工具，它會使用 4020，而不會使用 4021。  
  
 此埠可從命令列設定： **Msvsmon/wow64port \<port number> **。  
  
## <a name="the-discovery-port"></a>探索連接埠  
 UDP 3702 用於在網路上搜尋遠端偵錯工具的執行個體 (例如 [附加至處理序] **** 對話方塊中的 [尋找] **** 對話方塊)。 它只適用於探索執行遠端偵錯工具的機器，因此如果您有其他方式得知目標電腦的機器名稱或 IP 位址，它是選擇性的。 這是探索的標準連接埠，因此不能設定連接埠號碼。  
  
 如果您不想啟用探索，可以從命令列啟動 msvsmon 並停用探索：  **Msvsmon /nodiscovery**。  
  
## <a name="remote-debugger-ports-on-azure"></a>Azure 上的遠端偵錯工具連接埠  
 Azure 上的遠端偵錯工具會使用下列連接埠。 雲端服務上的連接埠會對應至個別 VM 上的連接埠。 所有連接埠都是 TCP。  

|**[連接]**|**雲端服務上的連接埠**|**VM 上的連接埠**|  
|-|-|-|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯](../debugger/remote-debugging.md)
