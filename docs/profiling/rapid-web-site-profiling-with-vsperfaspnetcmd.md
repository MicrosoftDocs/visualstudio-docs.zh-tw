---
title: 使用 VSPerfASPNETCmd 快速進行網站程式碼剖析 | Microsoft Docs
description: 瞭解 VSPerfASPNETCmd 命令列工具如何讓您輕鬆地分析 ASP.NET 的 web 應用程式。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a08604b95f49f55a5fea254447046d305d8feff9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720419"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>使用 VSPerfASPNETCmd 快速進行網站分析

**VSPerfASPNETCmd** 命令列工具可讓您輕鬆地分析 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式。 與 [VSPerfCmd](../profiling/vsperfcmd.md) 命令列工具相較之下，選項變少，無須設定任何環境變數，也不需要重新啟動電腦。 使用獨立分析工具進行程式碼剖析慣用的方法是使用 **VSPerfASPNETCmd**。 如需詳細資訊，請參閱[如何：安裝獨立分析工具](../profiling/how-to-install-the-stand-alone-profiler.md)。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

 在某些情況下，像是收集並行資料或暫停和繼續程式碼剖析時，慣用的程式碼剖析方法是使用 **VSPerfCmd**。

> [!NOTE]
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。

## <a name="profile-an-aspnet-application"></a>為 ASP.NET 應用程式進行分析

若要對 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式進行分析，請鍵入下列各節所述的其中一個命令。 網站隨即啟動，且分析工具會開始收集資料。 使用您的應用程式，然後關閉瀏覽器。 若要停止進行程式碼剖析，請在命令提示字元視窗中，按 **Enter** 鍵。

> [!NOTE]
> 根據預設，不會在 **vsperfaspnetcmd** 命令之後傳回命令提示字元。 您可以使用 **/nowait** 選項以強制傳回命令提示字元。 請參閱[使用 /NoWait 選項](#use-the-nowait-option)。

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>使用取樣方法收集應用程式統計資料
 取樣是 **VSPerfASPNETCmd** 工具的預設程式碼剖析方法，並不需要在命令列上指定。 下列命令列會從指定的 Web 應用程式收集應用程式統計資料︰

 **vsperfaspnetcmd**  *websiteUrl*

 一個本機伺服器裝載的 *websiteUrl* 範例可能為 *http://localhost/MySite/default.aspx*。 外部網站的範例為 *http://www.contoso.com* 。 如需詳細資訊，請參閱[對網站進行分析，但不在 Visual Studio 中開啟專案](how-to-collect-performance-data-for-a-web-site.md#to-profile-a-web-site-without-opening-a-project-in-visual-studio)。

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>使用檢測方法收集詳細的計時資料

使用下列命令列從動態編譯的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式收集詳細的計時資料︰

**vsperfaspnetcmd /trace**  *websiteUrl*

如果您想要分析靜態編譯的。在 web 應用程式中的 *dll* 檔案，您必須使用 [VSInstr](../profiling/vsinstr.md) 命令列工具來檢測檔案。 vsperfaspnetcmd /trace 命令會包含已檢測檔案中的資料。

## <a name="to-collect-net-memory-data"></a>收集 .NET 記憶體資料

**/Memory** 選項收集 .NET 記憶體中物件配置的相關資料，並可以收集這些物件存留期的相關資料。 收集配置資料是 **/Memory** 資料選項的預設模式，並不需要在命令列上指定。

 **vsperfaspnetcmd /memory** *websiteUrl*

 使用 **Lifetime** 參數可收集物件存留期資料，還有配置資料︰

 **vsperfaspnetcmd /memory:lifetime** *websiteUrl*

 您也可以使用 **/Trace** 選項，包含有關 .NET 記憶體資料的詳細計時資訊︰

 **vsperfaspnetcmd /memory**[**:lifetime**] **/trace**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>收集階層互動資料

> [!WARNING]
> 階層互動分析 (TIP) 資料可以使用任何版本的 Visual Studio 來收集。 不過，階層互動分析資料只能在 Visual Studio Enterprise 中檢視。
>
> 若要在 Windows 8 或 Windows Server 2012 上收集 TIP 資料，您必須使用檢測 (**/trace**) 選項。

透過取樣資料收集階層互動資料：

**vsperfaspnetcmd /tip** `websiteUrl`

透過檢測資料收集階層互動資料：

**vsperfaspnetcmd /trace /tip** *websiteUrl*

透過 .NET 記憶體資料收集階層互動資料：

**vsperfaspnetcmd /memory**[**:lifetime**] **/tip**_websiteUrl_

## <a name="use-the-nowait-option"></a>使用 /NoWait 選項

根據預設，不會在 **vsperfaspnetcmd** 命令之後傳回命令提示字元。 您可以使用下列語法選項以強制傳回命令提示字元。 接著，您可以在命令提示字元視窗中執行其他作業。 若要結束程式碼剖析，請在個別的 **vsperfaspnetcmd** 命令中使用 **/shutdown** 選項。

開始進行程式碼剖析：

**vsperfaspnetcmd** [*/Options*] **/nowait**_websiteUrl_

結束程式碼剖析：

**vsperfaspnetcmd /shutdown** *websiteUrl*

## <a name="additional-options"></a>其他選項

您可以將本節中的任何下列選項加入至稍早所列的命令，但 **vsperfaspnetcmd /shutdown** 命令除外。

|選項|描述|
|------------|-----------------|
|**/Output：**`VspFile`|根據預設，會使用檔案名稱 **PerformanceReport.vsp** 在目前目錄中建立程式碼剖析資料 (.*vsp*) 檔案。 您可以使用 /output 選項指定不同的位置、 檔案名稱，或兩者。|
|**/PackSymbols:Off**|根據預設，VsPerfASPNETCmd 會將符號 (函式和參數名稱等等) 嵌入 .*vsp* 檔。 內嵌符號會讓程式碼剖析資料檔案變得非常大。 如果當您分析資料時，可以存取含有符號的 .*pdb* 檔案，請使用 /packsymbols:off 選項以停用內嵌符號。|
