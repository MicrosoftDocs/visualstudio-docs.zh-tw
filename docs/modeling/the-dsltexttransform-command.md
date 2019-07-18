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
ms.openlocfilehash: 89d83da450014ebf29e2882438d27f9284c9bbbb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63001433"
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