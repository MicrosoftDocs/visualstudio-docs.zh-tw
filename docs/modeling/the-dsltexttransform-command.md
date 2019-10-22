---
title: DslTextTransform 命令
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a303fc3ddb880402e3f998b2360122f6f056b757
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72605937"
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