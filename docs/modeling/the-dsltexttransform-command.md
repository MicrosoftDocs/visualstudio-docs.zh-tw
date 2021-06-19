---
title: DslTextTransform 命令
description: 瞭解 DslTextTransform 是用來呼叫 TextTransform.exe 的腳本，並使用一般選項來執行它。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65d1e1d02c5b7d13c2e86343c6307306542d00e2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388642"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform 命令
DslTextTransform 是呼叫 TextTransform.exe 的腳本，並使用一般選項來執行它。 您可以使用 DslTextTransformation 將專案的夜間組建自動化 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 。 如需詳細資訊，請參閱 [使用 TextTransform 公用程式產生](../modeling/generating-files-with-the-texttransform-utility.md)檔案。

 DslTextTransform 位於下列目錄：

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 您可以指定下列引數做為 DslTextTransform 的輸入：

- 網域模型專案的輸出目錄。

- 設計工具定義專案的輸出目錄。

- 文字模板檔案的位置。

  DslTextTransform 會使用預設指示詞處理器和元件來處理指定的文字模板檔案。 如果您建立自訂指示詞處理器，您可以建立自己的批次檔來呼叫 TextTransform.exe。 在這個批次檔中，您可以指定元件和相關聯的自訂指示詞處理器。
