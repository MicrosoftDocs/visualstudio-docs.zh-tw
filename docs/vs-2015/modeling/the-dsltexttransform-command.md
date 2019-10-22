---
title: DslTextTransform 命令 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 599bf14a3d37fbd6bdff111f79e658f44624792b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658468"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform 命令
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform 是一個腳本，它會呼叫 TextTransform 並以一般選項執行。 您可以使用 DslTextTransformation 將 [!INCLUDE[dsl](../includes/dsl-md.md)] 專案的夜間組建自動化。 如需詳細資訊，請參閱[使用 TextTransform 公用程式產生](../modeling/generating-files-with-the-texttransform-utility.md)檔案。

 DslTextTransform 位於下列目錄：

 **\<Visual Studio SDK 安裝路徑 > \VisualStudioIntegration\Tools\Bin**

 您可以指定下列引數做為 DslTextTransform 的輸入：

- 網域模型專案的輸出目錄。

- 設計工具定義專案的輸出目錄。

- 文字模板檔案的位置。

  DslTextTransform 會使用預設指示詞處理器和元件來處理指定的文字模板檔案。 如果您建立自訂指示詞處理器，您可以建立自己的批次檔來呼叫 TextTransform。 在這個批次檔中，您可以指定元件和相關聯的自訂指示詞處理器。
