---
title: DslTextTransform 命令
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 97ddf1fb9dd9e59c2d00f3733069a5cdb14553bf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037898"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform 命令
DslTextTransform.cmd 是指令碼呼叫 TextTransform.exe 並執行常見的選項。 您可用來自動化的夜間組建 DslTextTransformation.cmd 您[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]專案。 如需詳細資訊，請參閱 <<c0> [ 產生的檔案，使用 TextTransform 公用程式](../modeling/generating-files-with-the-texttransform-utility.md)。

 DslTextTransform.cmd 位於下列目錄：

 **\<Visual Studio SDK 安裝路徑 > \VisualStudioIntegration\Tools\Bin**

 您可以指定下列引數做為 DslTextTransform.cmd 輸入：

- 網域模型專案的輸出目錄。

- 設計工具定義專案的輸出目錄。

- 文字範本檔案的位置。

  DslTextTransform.cmd 處理使用的預設指示詞處理器和組件指定的文字範本檔案。 如果您建立自訂指示詞處理器，您可以建立您自己呼叫 TextTransform.exe 的批次檔。 在此批次檔中，您可以指定您的組件和相關聯的自訂指示詞處理器。