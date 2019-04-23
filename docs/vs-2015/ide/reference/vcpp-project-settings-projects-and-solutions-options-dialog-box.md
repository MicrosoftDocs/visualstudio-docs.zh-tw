---
title: 選項對話方塊、專案和方案、VC++ 專案設定 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 66110f6544bc19476bb4ecdfd6929fb4e26f0b52
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082430"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>選項對話方塊、專案和方案、VC++ 專案設定
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

此對話方塊可讓您定義與建置記錄及支援檔案類型相關的 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 專案設定。  
  
### <a name="to-access-this-dialog-box"></a>若要存取此對話方塊  
  
1. 在 [ **工具** ] 功能表上按一下 [ **選項**]。  
  
2. 選取 [專案和方案]，然後選取 [VC++ 專案設定]。  
  
## <a name="build-customization-search-path"></a>建置自訂搜尋路徑  
 指定包含 .rules 檔案的目錄清單，以協助您定義專案的建置規則。  
  
## <a name="build-logging"></a>建置記錄  
 **是**  
 開啟組建記錄檔的產生。 此選項會產生 BuildLog.htm，您可以在專案的中繼檔案目錄中找到此檔案。 每個全新的組建都會覆寫上一個 BuildLog.htm 檔案。  
  
 **No**  
 關閉組建記錄檔的產生。  
  
## <a name="build-timing"></a>建置執行時間  
 **是**  
 開啟建置執行時間。 如果選取，組建完成所需的時間會發佈到 [輸出] 視窗。 如需詳細資訊，請參閱[輸出視窗](../../ide/reference/output-window.md)。  
  
 **No**  
 關閉建置執行時間。  
  
## <a name="extensions-to-hide"></a>要隱藏的副檔名  
 指定啟用 [顯示所有檔案] 時，不會顯示在方案總管中之檔案的副檔名。  
  
## <a name="extensions-to-include"></a>要包含的副檔名  
 指定可移植到您專案中之檔案的副檔名。  
  
## <a name="maximum-concurrent-c-compilations"></a>並行 C++ 編譯的最大數目  
 指定要用於並行 C++ 編譯的最大 CPU 核心數目。  
  
## <a name="show-environment-in-log"></a>在記錄中顯示環境  
 **是**  
 列出組建記錄檔中的環境變數。 此選項會指定將 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 專案建置期間的所有環境變數，反映到組建記錄檔中。  
  
 **No**  
 從組建記錄檔排除環境變數。  
  
## <a name="solution-explorer-mode"></a>方案總管模式  
 **僅顯示專案中的檔案**  
 將方案總管設定為僅顯示專案中的檔案。  
  
 **顯示所有檔案**  
 將方案總管設定為顯示專案中的檔案，以及專案資料夾中磁碟上的檔案。  
  
## <a name="see-also"></a>請參閱  
 [建置 C/C++ 程式](http://msdn.microsoft.com/library/fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008)   
 [C/C++ 建置參考](http://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)
