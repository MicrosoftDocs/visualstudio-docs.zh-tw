---
title: 指定程式碼剖析命令列工具的路徑
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fb445e23b5d507bafb7fece40bf606bbfb76c370
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809181"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>指定分析工具命令列工具的路徑

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼分析工具命令列工具的路徑不會加入 PATH 環境變數中。 在 32 位元電腦上，這些工具會在一個目錄中。 在 64 位元電腦上，程式碼分析工具有 32 位元和 64 位元兩種版本。

## <a name="32-bit-computers"></a>32 位元電腦

針對機器碼，Visual Studio 分析工具 API 位在 *VSPerf.dll* 中。 標頭檔 (*VSPerf.h*) 和匯入程式庫 (*VSPerf.lib*) 位在 *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK* 目錄中。

 針對 managed 程式碼，profiler Api 位於 *Microsoft.VisualStudio.Profiler.dll*中。 這個 DLL 位於 *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools* 目錄。

## <a name="64-bit-computers"></a>64 位元電腦

在 64 位元電腦上，則會根據已進行程式碼剖析之應用程式的目標平台指定路徑。

- 若是 32 位元應用程式，預設程式碼剖析工具目錄是：

      (原生) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK*
     
      (受控) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- 若是 64 位元應用程式，預設程式碼剖析工具目錄是：

      (原生) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK*

      (受控) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
