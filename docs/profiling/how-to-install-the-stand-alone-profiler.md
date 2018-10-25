---
title: 如何：安裝獨立分析工具 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 55c9e7c6ec4a34d59c45b2a56abedaa6d3fd2974
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942436"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>如何：安裝獨立分析工具
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 提供命令列型獨立分析工具，不用安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 即可執行。 當電腦未安裝或無法安裝開發環境時，就會發生這種情況。 例如，您不應該在生產環境的網頁伺服器上安裝開發環境。  
  
> [!NOTE]
>  當您要使用獨立的分析工具收集 ASP.NET 網站的效能資料時，建議您使用 [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) 命令列工具，不要用 [VSPerfCmd](../profiling/vsperfcmd.md) 工具。  
  
### <a name="to-install-the-stand-alone-profiler"></a>安裝獨立分析工具  
  
1. 在包含 *\Standalone Profiler* 路徑的目錄中，找到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 安裝媒體的獨立分析工具安裝程式 (*vs_profiler.exe*)，並執行它。  
  
2. 將 *vsintr.exe* 和 *msdis150.dll* 的路徑新增至系統路徑。  
  
   > [!NOTE]
   >  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的預設安裝中，*vsinstr.exe* 和 *msdis150.dll* 位於 *\Program Files\Visual Studio 10\Team Tools\Performance Tools*。  
  
3. 在命令提示字元處，鍵入 **VSInstr**。  
  
   > [!NOTE]
   >  如果顯示 vsinstr.exe 的使用資訊，即表示所有項目設定正確。 如果看到有錯誤指出找不到 vsinstr.exe 或它其中一個相依性，請確定是否依步驟 2 所述正確設定路徑。  
  
4. 將 **_NT_SYMBOL_PATH** 變數設為 **symsrv\*symsrv.dll\*c:\localcache\*http://msdl.microsoft.com/download/symbols**，以設定符號伺服器  
  
5. 使用系統環境變數設定好符號伺服器之後，在新的命令提示字元處執行命令列分析工具。 這可讓新的環境變數生效。 在命令提示字元視窗中，鍵入下列命令：  
  
    **start %COMSPEC%**  
  
   > [!NOTE]
   >  如需如何設定符號伺服器套件的詳細指示，請參閱[如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)。  
  
6. 使用 [VSPerfReport](../profiling/vsperfreport.md) 工具將符號序列化成分析資料 (.vsp) 檔案。 使用 **VSPerfReport /summary:all /packsymbols** 參數。 如未在資料檔案中插入符號，請確定設定了 _NT_SYMBOL_PATH 環境變數。  
  
## <a name="see-also"></a>另請參閱  
 [從命令列進行分析](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [逐步解說：使用取樣進行命令列分析](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [逐步解說：使用檢測進行命令列分析](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)