---
title: 使用 SuppressMessage 屬性隱藏警告 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- VC.Project.VCFxCopTool.InputAssemblyFileName
- VC.Project.VCFxCopTool.FxCopModuleSuppressionsFile
- VC.Project.VCFxCopTool.FxCopUseTypeNameInSuppression
- VC.Project.VCFxCopTool.OutputFile
helpviewer_keywords:
- code analysis, source suppression
- source suppression
- SuppressMessage attribute
- code analysis, SuppressMessage attribute
ms.assetid: a38c57a2-d29d-43c0-84ff-3308b2484ce6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8df4972cb1d54b88d6e716254574ea95bcaed4b7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672434"
---
# <a name="suppress-warnings-by-using-the-suppressmessage-attribute"></a>使用 SuppressMessage 屬性隱藏警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指出警告是 nonapplicable 的，這通常很有用，讓小組成員知道程式碼已經過審核，並判定警告應該隱藏起來。 在來源隱藏專案（ISS）中，可讓開發人員將隱藏警告的屬性，放在產生警告的位置附近。 您可以將 ISS 屬性直接加入至原始檔，也可以使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 中的快捷方式功能表。

## <a name="in-this-section"></a>本章節內容

|||
|-|-|
|[原始檔中隱藏項目概觀](../code-quality/in-source-suppression-overview.md)|瞭解 ISS，以及如何在您的程式碼中使用它。|
|[如何：使用功能表項目隱藏警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)|瞭解如何使用快捷方式功能表來隱藏 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 中的警告。|

## <a name="related-sections"></a>相關章節
 [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
