---
title: "選項對話方塊、專案和方案、VC++ 專案設定 | Microsoft Docs"
ms.custom: 
ms.date: 08/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7f24c1cd65d4669f326f866fbc04160d32daa4a1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>選項對話方塊、專案和方案、VC++ 專案設定
此對話方塊可讓您定義與記錄、效能和支援檔案類型相關的 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 組建和專案設定。  
  
### <a name="to-access-this-dialog-box"></a>若要存取此對話方塊  
  
1.  在 [ **工具** ] 功能表上按一下 [ **選項**]。  
  
2.  選取 [專案和方案]，然後選取 [VC++ 專案設定]。  
 
## <a name="build-logging"></a>建置記錄  
 **是**  
  開啟組建記錄檔的產生。 此選項會產生 BuildLog.htm，您可以在專案的中繼檔案目錄中找到此檔案。 每個全新的組建都會覆寫上一個 BuildLog.htm 檔案。  
  
 **No**  
  關閉組建記錄檔的產生。  

## <a name="show-environment-in-log"></a>在記錄中顯示環境  
 **是**  
 列出組建記錄檔中的環境變數。 此選項會指定將 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 專案建置期間的所有環境變數，反映到組建記錄檔中。  
  
 **No**  
 從組建記錄檔排除環境變數。  

## <a name="build-timing"></a>建置執行時間  
 **是**  
  開啟建置執行時間。 如果選取，組建完成所需的時間會發佈到 [輸出] 視窗。 如需詳細資訊，請參閱[輸出視窗](../../ide/reference/output-window.md)。  
  
 **No**  
 關閉建置執行時間。  
   
## <a name="maximum-concurrent-c-compilations"></a>並行 C++ 編譯的最大數目  
  指定要用於並行 C++ 編譯的最大 CPU 核心數目。  
  
## <a name="extensions-to-include"></a>要包含的副檔名  
  指定可移植到您專案中之檔案的副檔名。  

## <a name="extensions-to-hide"></a>要隱藏的副檔名  
  指定啟用 [顯示所有檔案] 時，不會顯示在方案總管中之檔案的副檔名。  

 ## <a name="build-customization-search-path"></a>建置自訂搜尋路徑  
  指定包含 .rules 檔案的目錄清單，以協助您定義專案的建置規則。  

# <a name="solution-explorer-mode"></a>方案總管模式  
 **僅顯示專案中的檔案**  
  將方案總管設定為僅顯示專案中的檔案。  
  
 **顯示所有檔案**  
  將方案總管設定為顯示專案中的檔案，以及專案資料夾中磁碟上的檔案。  

## <a name="enable-project-caching"></a>啟用專案快取
**是**  
讓 Visual Studio 能夠快取專案資料，以便在您下次開啟專案時，載入那份快取的資料，而不必從專案檔重新計算資料。 使用快取資料可以大幅加速專案載入時間。   

**No**  
不使用快取的專案資料。 每次載入專案時都會剖析專案檔。

## <a name="see-also"></a>另請參閱  
 [建置 C/C++ 程式](/cpp/build/building-c-cpp-programs)   
 [C/C++ 建置參考](/cpp/build/reference/c-cpp-building-reference)