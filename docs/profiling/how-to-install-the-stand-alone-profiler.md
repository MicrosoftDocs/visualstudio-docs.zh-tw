---
title: 安裝獨立分析工具 | Microsoft Docs
description: 瞭解如何安裝獨立分析工具，這可在未安裝 Visual Studio 的情況下執行。 在某些情況下，Visual Studio 不應該安裝。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8f13edc60a2c05d50e2118e24344bf9d475e3f5f
ms.sourcegitcommit: 8e15b434bf5db3e0f719320ca82682df1a3da110
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98883614"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>如何：安裝獨立分析工具
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 提供命令列型獨立分析工具，不用安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 即可執行。 當電腦未安裝或無法安裝開發環境時，就會發生這種情況。 例如，您不應該在生產環境的網頁伺服器上安裝開發環境。

> [!NOTE]
> 當您要使用獨立的分析工具收集 ASP.NET 網站的效能資料時，建議您使用 [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) 命令列工具，不要用 [VSPerfCmd](../profiling/vsperfcmd.md) 工具。

### <a name="to-install-the-stand-alone-profiler"></a>安裝獨立分析工具

1. 下載 [Visual Studio 效能工具](https://visualstudio.microsoft.com/downloads/?q=performance+tools#performance-tools-for-visual-studio)。

1. 在您下載效能工具處找到獨立分析工具安裝程式 (*vs_standaloneprofiler.exe*) 並執行它。

2. 將 *vsinstr.exe* 的路徑新增至系統路徑。

   > [!NOTE]
   > 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。

3. 在命令提示字元處，鍵入 **VSInstr**。

   > [!NOTE]
   > 如果顯示 vsinstr.exe 的使用資訊，即表示所有項目設定正確。 如果看到有錯誤指出找不到 vsinstr.exe 或它其中一個相依性，請確定是否依步驟 2 所述正確設定路徑。

4. 將 **_NT_SYMBOL_PATH** 變數設為 **symsrv\*symsrv.dll\*c:\localcache\*https://msdl.microsoft.com/download/symbols**，以設定符號伺服器

5. 使用系統環境變數設定好符號伺服器之後，在新的命令提示字元處執行命令列分析工具。 這可讓新的環境變數生效。 在命令提示字元視窗中，鍵入下列命令：

    **start %COMSPEC%**

   > [!NOTE]
   > 如需有關如何設定符號伺服器套件的詳細指示，請參閱 [如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)。

6. 使用 [VSPerfReport](../profiling/vsperfreport.md) 工具將符號序列化成分析資料 (.vsp) 檔案。 使用 **VSPerfReport /summary:all /packsymbols** 參數。 如未在資料檔案中插入符號，請確定設定了 _NT_SYMBOL_PATH 環境變數。

## <a name="see-also"></a>另請參閱
- [從命令列進行分析](../profiling/using-the-profiling-tools-from-the-command-line.md)
- [逐步解說：使用檢測進行命令列分析](command-line-profiling-of-stand-alone-applications.md)
- [如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)
- [VSPerfReport](../profiling/vsperfreport.md)
