---
title: VSPerfASPNetCmd | Microsoft Docs
description: 瞭解 VSPerfASPNetCmd.exe 命令列工具如何讓您分析 ASP.Net 網站，而不需要設定環境變數或重新開機電腦。
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b594141d6209c8ede9171df880e7523b81a34775
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719223"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
**VSPerfASPNetCmd.exe** 命令列工具可讓您進行 ASP.Net 網站分析，而不需要設定環境變數或重新啟動您的電腦。 當您進行 ASP.NET 網站分析且不需要 **VSPerfCmd** 提供的額外功能時，請使用 **VSPerfASPNetCmd.exe** 而非 [VSPerfCmd](../profiling/vsperfcmd.md)。 如需 **VSPerfASPNetCmd** 的詳細資訊，請參閱 [使用 VSPerfASPNetCmd 快速進行網站分析](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)。 當您使用獨立分析工具來分析 ASP.NET 的網站時， **VSPerfASPNetCmd** 是慣用的命令列工具。

## <a name="syntax"></a>Syntax
 **vsperfaspnetcmd** [/*Options*] *Website*

## <a name="options"></a>選項。

|選項|描述|
|------------|-----------------|
|**/Sample** 或 **/s**|使用取樣方法進行網站分析。 **/Sample** 是預設方法。 /Sample 無法搭配 **/Trace** 使用。|
|**/Trace** 或 **/t**|使用檢測方法進行網站分析。 /Trace 無法搭配 **/Sample** 使用。|
|**/Memory**[**：** `Type` ] 或 **/m**[**：**{**a**&#124;**l**}]|分析記憶體配置，以及選擇性地分析物件存留期 (記憶體回收)。 **/Memory** 可以搭配取樣或檢測方法使用。<br /><br /> *Type* 可以是下列其中之一：<br /><br /> -   **allocation** (或 **a**) 只會收集記憶體配置資料。<br />-   **lifetime** (或 **l**) 會收集記憶體配置和物件存留期資料。<br /><br /> `Type` 預設為 **allocation**。|
|**/Tip** 或 **/i**|將詳細 ASP.NET 要求和 ADO.NET 呼叫資訊加入至分析資料。 **/Tip** 可以搭配取樣或檢測方法使用，且可與 **/Memory** 選項一起使用。|
|**/Output:** `File` 或 **/o:**`File`|指定分析資料 ( 的路徑和檔案名。*.vsp*) 檔。|
|**/NoWait** 或 **/n**|立即傳回命令提示字元，以便在 [命令提示字元] 視窗中使用其他命令。 您必須在個別的命令列上輸入 **VSPerfASPNETCmd /Shutdown** 以關閉分析。|
|**/PackSymbols**[:{**on**&#124;**off**} 或 **/p**[:{**on**&#124;**off**}|在分析資料 (*.vsp*) 檔案中內嵌符號 (函式與參數名稱等)。|
|**/Shutdown:** `Website` 或 **/d:**`Website`|關閉分析。 在使用 **/NoWait** 選項啟動分析之後，或者分析工具非預期地結束時，作為命令列上的唯一選項使用。 指定您在原始 **VSPerfASPNETCmd** 命令中使用的相同 URL。|
|`Website`|要分析之網站的 URL。|

## <a name="see-also"></a>另請參閱
- [使用 VSPerfASPNETCmd 快速進行網站分析](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
- [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
