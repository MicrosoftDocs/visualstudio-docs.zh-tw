---
title: C++ 專案設定選項
description: 瞭解如何使用 [專案和方案] 區段中的 [VC + + 專案設定] 頁面，來定義與記錄、效能和支援檔案類型相關的 c + + 組建和專案設定。
ms.custom: SEO-VS-2020
ms.date: 08/02/2017
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
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 16226cd66c2cf46d1dc46f1cb3f90dc3bad9658c
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616274"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>選項對話方塊、專案和方案、VC++ 專案設定

此對話方塊可讓您定義與記錄、效能和支援檔案類型相關的 C++ 組建和專案設定。

## <a name="to-access-this-dialog-box"></a>若要存取此對話方塊

1. 在 **[工具]** 功能表上，按一下 **[選項]** 。

2. 選取 [專案和方案]，然後選取 [VC++ 專案設定]。

## <a name="build-logging"></a>建置記錄

 **是**

  開啟組建記錄檔的產生。 此選項會產生 BuildLog.htm，您可以在專案的中繼檔案目錄中找到此檔案。 每個全新的組建都會覆寫上一個 BuildLog.htm 檔案。

 **否**

  關閉組建記錄檔的產生。

## <a name="show-environment-in-log"></a>在記錄中顯示環境

 **是**

列出組建記錄檔中的環境變數。 此選項會指定將 C++ 專案建置期間的所有環境變數，反映到建置記錄檔中。

 **否**

從組建記錄檔排除環境變數。

## <a name="build-timing"></a>建置執行時間

 **是**

  開啟建置執行時間。 如果選取，組建完成所需的時間會發佈到 [輸出] 視窗。 如需詳細資訊，請參閱 [輸出視窗](../../ide/reference/output-window.md)。

 **否**

關閉建置執行時間。

## <a name="maximum-concurrent-c-compilations"></a>並行 C++ 編譯的最大數目

指定要用於並行 C++ 編譯的最大 CPU 核心數目。

## <a name="extensions-to-include"></a>要包含的副檔名

指定可移植到您專案中之檔案的副檔名。

## <a name="extensions-to-hide"></a>要隱藏的副檔名

指定啟用 [顯示所有檔案] 時，不會顯示在方案總管中之檔案的副檔名。

## <a name="build-customization-search-path"></a>建置自訂搜尋路徑

指定包含 .rules 檔案的目錄清單，以協助您定義專案的建置規則。

## <a name="solution-explorer-mode"></a>方案總管模式

**僅顯示專案中的檔案**

將方案總管設定為僅顯示專案中的檔案。

**顯示所有檔案**

將方案總管設定為顯示專案中的檔案，以及專案資料夾中磁碟上的檔案。

## <a name="enable-project-caching"></a>啟用專案快取

**是**

讓 Visual Studio 能夠快取專案資料，以便在您下次開啟專案時，載入那份快取的資料，而不必從專案檔重新計算資料。 使用快取資料可以大幅加速專案載入時間。

**否**

不使用快取的專案資料。 每次載入專案時都會剖析專案檔。

## <a name="see-also"></a>另請參閱

- [建置 C/C++ 程式](/cpp/build/projects-and-build-systems-cpp)
- [C/C++ 建置參考](/cpp/build/reference/c-cpp-building-reference)