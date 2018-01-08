---
title: "DslTextTransform 命令 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: "30"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 4b8c7040cabf05b30920654996891bc8d19f42db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform 命令
DslTextTransform.cmd 是指令碼呼叫 TextTransform.exe 並執行常見的選項。 您可用來自動化的夜間組建 DslTextTransformation.cmd 您[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]專案。 如需詳細資訊，請參閱[使用 TextTransform 公用程式產生的檔案](../modeling/generating-files-with-the-texttransform-utility.md)。  
  
 DslTextTransform.cmd 位於下列目錄：  
  
 **\<Visual Studio SDK 安裝路徑 > \VisualStudioIntegration\Tools\Bin**  
  
 您可以指定下列引數做為 DslTextTransform.cmd 輸入：  
  
-   網域模型專案的輸出目錄。  
  
-   設計工具定義中專案輸出目錄。  
  
-   文字範本檔的位置。  
  
 DslTextTransform.cmd 處理指定的文字範本檔使用的預設指示詞處理器和組件。 如果您建立自訂指示詞處理器，您可以建立您自己呼叫 TextTransform.exe 的批次檔。 在此批次檔中，您可以指定您的組件和相關聯的自訂指示詞處理器。