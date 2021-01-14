---
title: 遠端偵錯程式埠指派 |Microsoft Docs
description: 瞭解 Visual Studio 32 位作業系統、64位作業系統和 Azure 上的遠端偵錯程式埠指派。 瞭解探索埠。
ms.custom: SEO-VS-2020
ms.date: 05/18/2018
ms.topic: reference
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40081f276dc9649cf448bf00e80d11fc80f58f47
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204822"
---
# <a name="remote-debugger-port-assignments"></a>遠端偵錯工具連接埠指派
Visual Studio 遠端偵錯工具可以應用程式或背景服務的形式執行。 當以應用程式的形式執行時，它會使用預設指派的連接埠，如下所示：
::: moniker range=">=vs-2019"
- Visual Studio 2019：4024
::: moniker-end
- Visual Studio 2017：4022

- Visual Studio 2015：4020

- Visual Studio 2013：4018

- Visual Studio 2012：4016

換句話說，指派給遠端偵錯工具的連接埠號碼會隨著每個版本遞增 2。 您可以視需要設定不同的埠號碼。 我們將在稍後的章節中說明如何設定連接埠號碼。

## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>32 位元作業系統上的遠端偵錯工具連接埠

::: moniker range=">=vs-2019"
 TCP 4024 (在 Visual Studio 2019 中) 是主要的連接埠，在所有情況下都需要。 您可以從命令列或遠端偵錯工具視窗來進行此設定。
::: moniker-end
::: moniker range="vs-2017"
 (在 Visual Studio 2017 中) TCP 4022 是主要的連接埠，在所有情況下都需要。 您可以從命令列或遠端偵錯工具視窗來進行此設定。
::: moniker-end

 在遠端偵錯工具視窗中，按一下 [工具] > [選項]，然後設定 TCP/IP 連接埠編號。

 在命令列上，使用 **/port** 參數啟動遠端偵錯程式： **msvsmon/port \<port number>**。

 您可以在遠端偵錯說明中找到所有遠端偵錯工具命令列參數 (在遠端偵錯工具視窗中按 **F1** 或按一下 [說明] > [用法])。

## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>64 位元作業系統上的遠端偵錯工具連接埠
::: moniker range=">=vs-2019"
 啟動遠端偵錯程式的64位版本時，預設會使用主要端口 (4024) 。  如果您要對32位的進程進行偵錯工具，64位版本的遠端偵錯程式會在埠4025上啟動遠端偵錯程式的32位版本 (1) 遞增的主要端口號碼。 如果您執行 32 位元遠端偵錯工具，它會使用 4024，而不會使用 4025。
::: moniker-end
::: moniker range="vs-2017"
 啟動遠端偵錯程式的64位版本時，預設會使用主要端口 (4022) 。  如果您要對32位的進程進行偵錯工具，64位版本的遠端偵錯程式會在埠4023上啟動遠端偵錯程式的32位版本 (1) 遞增的主要端口號碼。 如果您執行 32 位元遠端偵錯工具，它會使用 4022，而不會使用 4023。
:::moniker-end

 此埠可從命令列設定： **Msvsmon/wow64port \<port number>**。

## <a name="the-discovery-port"></a>探索連接埠
 UDP 3702 用於在網路上搜尋遠端偵錯工具的執行個體 (例如 [附加至處理序]  對話方塊中的 [尋找]  對話方塊)。 它只適用於探索執行遠端偵錯工具的機器，因此如果您有其他方式得知目標電腦的機器名稱或 IP 位址，它是選擇性的。 這是探索的標準連接埠，因此不能設定連接埠號碼。

 如果您不想啟用探索，可以從命令列啟動 msvsmon 並停用探索：  **Msvsmon /nodiscovery**。

## <a name="remote-debugger-ports-on-azure"></a>Azure 上的遠端偵錯工具連接埠
 Azure 上的遠端偵錯工具會使用下列連接埠。 雲端服務上的連接埠會對應至個別 VM 上的連接埠。 所有連接埠都是 TCP。

|連線|雲端服務上的連接埠|VM 上的連接埠|
|-|-|-|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarderx86|31401|31399|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|

## <a name="see-also"></a>請參閱
- [遠端偵錯](../debugger/remote-debugging.md)
