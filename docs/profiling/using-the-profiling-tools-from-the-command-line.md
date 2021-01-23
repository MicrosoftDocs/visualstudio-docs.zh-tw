---
title: 從命令列使用程式碼剖析工具 | Microsoft Docs
description: 使用 Visual Studio 分析工具的命令列工具來分析應用程式，並使用批次檔和腳本來自動進行程式碼剖析。
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9d6e159e28a1401548f0cda7b795a5bbe70a257b
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723227"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>從命令列使用分析工具
您可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具的命令列工具，在命令提示字元分析應用程式，並使用批次檔和指令碼將程式碼剖析自動化。 您也可以在命令提示字元產生報告檔。 您可以使用輕量型獨立分析工具，在未安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的的電腦上收集資料。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

## <a name="common-tasks"></a>常見工作

| Task | 相關內容 |
| - | - |
| **設定符號的位置：** 若要顯示函式和參數的名稱，分析工具必須具有符號 ( 的存取權。已分析之二進位檔的 *pdb*) 檔案。 這些檔案應該包含 Microsoft 作業系統的符號檔，以及您想要在分析中檢視的應用程式。 您可以使用公用 Microsoft 符號伺服器，確定您有正確的。Microsoft 二進位檔的 *pdb* 檔案。 | -   [如何：從命令列指定符號檔位置](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **分析應用程式：** 您用來分析目標應用程式的命令列工具與選項，取決於應用程式的類型、程式碼剖析工具以及目標為 Managed 或原生應用程式。 | -   [從命令列使用分析方法](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [設定檔服務](../profiling/command-line-profiling-of-services.md) |
| **建立 .xml 和 .csv 報表：** 在命令提示自原進行程式碼剖析，會建立可在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的介面中檢視的資料檔案。 您也可以產生。 ( 的 *xml* 或逗點分隔值。使用 VSPerfReport 命令列工具的 *csv*) 資料檔案。 | -   [從命令列建立分析工具報告](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md) |
| **在沒有 Visual Studio 的電腦上分析程式碼︰** 您可以使用程式碼剖析工具的獨立分析工具，在未安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的電腦上收集應用程式的資料。 | -   [如何：安裝獨立 profiler](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>參考
- [命令列分析工具參考](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>另請參閱
- [效能總管](../profiling/performance-explorer.md)
