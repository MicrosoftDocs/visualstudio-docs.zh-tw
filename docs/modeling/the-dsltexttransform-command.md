---
title: DslTextTransform 命令
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32c01401eda8fb1bbe2bdcfc2950a51b968e98b7
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114911"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform 命令
DslTextTransform 是一個腳本，它會呼叫 TextTransform 並以一般選項執行。 您可以使用 DslTextTransformation 將 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 專案的夜間組建自動化。 如需詳細資訊，請參閱[使用 TextTransform 公用程式產生](../modeling/generating-files-with-the-texttransform-utility.md)檔案。

 DslTextTransform 位於下列目錄：

 **\<Visual Studio SDK 安裝路徑 > \VisualStudioIntegration\Tools\Bin**

 您可以指定下列引數做為 DslTextTransform 的輸入：

- 網域模型專案的輸出目錄。

- 設計工具定義專案的輸出目錄。

- 文字模板檔案的位置。

  DslTextTransform 會使用預設指示詞處理器和元件來處理指定的文字模板檔案。 如果您建立自訂指示詞處理器，您可以建立自己的批次檔來呼叫 TextTransform。 在這個批次檔中，您可以指定元件和相關聯的自訂指示詞處理器。
