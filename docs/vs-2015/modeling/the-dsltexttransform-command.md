---
title: DslTextTransform 命令 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8a565fa6226348a1fe1b6dcfcbb67f704e74abc8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491791"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform 命令
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[DslTextTransform 命令](https://docs.microsoft.com/visualstudio/modeling/the-dsltexttransform-command)。  
  
DslTextTransform.cmd 是指令碼呼叫 TextTransform.exe 並執行常見的選項。 您可用來自動化的夜間組建 DslTextTransformation.cmd 您[!INCLUDE[dsl](../includes/dsl-md.md)]專案。 如需詳細資訊，請參閱 <<c0> [ 產生的檔案，使用 TextTransform 公用程式](../modeling/generating-files-with-the-texttransform-utility.md)。  
  
 DslTextTransform.cmd 位於下列目錄：  
  
 **\<Visual Studio SDK 安裝路徑 > \VisualStudioIntegration\Tools\Bin**  
  
 您可以指定下列引數做為 DslTextTransform.cmd 輸入：  
  
-   網域模型專案的輸出目錄。  
  
-   設計工具定義專案的輸出目錄。  
  
-   文字範本檔案的位置。  
  
 DslTextTransform.cmd 處理使用的預設指示詞處理器和組件指定的文字範本檔案。 如果您建立自訂指示詞處理器，您可以建立您自己呼叫 TextTransform.exe 的批次檔。 在此批次檔中，您可以指定您的組件和相關聯的自訂指示詞處理器。



