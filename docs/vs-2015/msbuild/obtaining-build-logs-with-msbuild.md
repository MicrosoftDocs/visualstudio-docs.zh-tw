---
title: 使用 MSBuild 取得組建記錄檔 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc6d3981b2c671eda2a121f698835dd7932894bf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500035"
---
# <a name="obtaining-build-logs-with-msbuild"></a>使用 MSBuild 取得組建記錄檔
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[使用 MSBuild 取得組建記錄檔](https://docs.microsoft.com/visualstudio/msbuild/obtaining-build-logs-with-msbuild)。  
  
  
將 MSBuild 與參數搭配使用，您可以指定想要檢閱的組建資料量，以及是否要將組建資料儲存至一或多個檔案。 您也可以指定自訂記錄器來收集組建資料。 如需本主題未涵蓋的 MSBuild 命令列參數相關資訊，請參閱[命令列參考](../msbuild/msbuild-command-line-reference.md)。  
  
> [!NOTE]
>  如果您使用 Visual Studio IDE 來建置專案，就能藉由檢視建置記錄檔來進行這些組建的疑難排解。 如需詳細資訊，請參閱[如何：檢閱、儲存和設定建置記錄檔](../ide/how-to-view-save-and-configure-build-log-files.md)。  
  
## <a name="setting-the-level-of-detail"></a>設定詳細層級  
 當您使用 MSBuild 來建置專案，但未指定詳細資料層級時，即會在輸出記錄檔中顯示下列資訊：  
  
-   已分類為高重要性的錯誤、警告和訊息。  
  
-   一些狀態事件。  
  
-   組建摘要。  
  
 使用 **/verbosity** (**/v**) 參數，您可以控制要在輸出記錄檔中顯示的資料量。 如需疑難排解，請使用 `detailed` (`d`) 或 `diagnostic` (`diag`) 的詳細資訊層級，其中提供了最多資訊。  
  
 當您將 **/verbosity** 設為 `detailed` 時，建置程序可能會變慢，而當您將 **/verbosity** 設為 `diagnostic` 時，甚至會變得更慢。  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## <a name="saving-the-build-log-to-a-file"></a>將建置記錄儲存至檔案  
 您可以使用 **/fileLogger** (**fl**) 參數，將組建資料儲存至檔案。 下列範例會將組建資料儲存至名為 `msbuild.log` 的檔案。  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 在下列範例中，會將記錄檔命名為 `MyProjectOutput.log`，並將記錄檔輸出的詳細資訊設為 `diagnostic`。 您可以使用 **/filelogparameters** (`flp`) 參數，來指定這兩個設定。  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 如需詳細資訊，請參閱[命令列參考](../msbuild/msbuild-command-line-reference.md)。  
  
## <a name="saving-the-log-output-to-multiple-files"></a>將記錄輸出儲存至多個檔案  
 下列範例會將整個記錄檔儲存至 `msbuild1.log`、只將錯誤儲存至 `JustErrors.log`，並且只將警告儲存至 `JustWarnings.log`。 這個範例會針對這三個檔案的每個檔案使用檔案號碼。 檔案號碼會指定於 **/fl** 和 **/flp** 參數 (例如，`/fl1` 和 `/flp1`) 的正後方。  
  
 適用於檔案 2 和 3 的 **/Filelogparameters** (`flp`) 參數會指定每個檔案的名稱，以及要在每個檔案中包含的項目。 由於未指定檔案 1 的名稱，因此會使用 `msbuild1.log` 的預設名稱。  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 如需詳細資訊，請參閱[命令列參考](../msbuild/msbuild-command-line-reference.md)。  
  
## <a name="using-a-custom-logger"></a>使用自訂記錄器  
 若要撰寫自己的記錄器，請編寫可實作 <xref:Microsoft.Build.Framework.ILogger> 介面的 Managed 類型。 例如，您可以使用自訂記錄器，透過電子郵件傳送建置錯誤、將其記錄至資料庫，或將其記錄至 XML 檔案。 如需詳細資訊，請參閱[組建記錄器](../msbuild/build-loggers.md)。  
  
 在 MSBuild 命令列中，您會使用 **/logger** 參數來指定自訂記錄器。 您也可以使用 **/noconsolelogger** 參數，來停用預設的主控台記錄器。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [組建記錄器](../msbuild/build-loggers.md)   
 [在多處理器環境中記錄](../msbuild/logging-in-a-multi-processor-environment.md)   
 [建立轉送記錄器](../msbuild/creating-forwarding-loggers.md)   
 [MSBuild 概念](../msbuild/msbuild-concepts.md)



