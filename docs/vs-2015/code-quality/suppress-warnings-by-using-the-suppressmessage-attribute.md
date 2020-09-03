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
ms.openlocfilehash: a5d64a27759cf844550297beb19b026bbeaa0e40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546818"
---
# <a name="suppress-warnings-by-using-the-suppressmessage-attribute"></a>使用 SuppressMessage 屬性隱藏警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

這通常很適合用來表示警告 nonapplicable，讓小組成員知道程式碼已經過審核，而且判斷出警告應該隱藏起來。 在原始檔隱藏 (ISS) 可讓開發人員將隱藏警告的屬性放在接近產生警告的位置。 您可以直接將 ISS 屬性新增至原始檔，也可以使用 IDE 中的快捷方式功能表 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。

## <a name="in-this-section"></a>本節內容

|標題|描述|
|-|-|
|[原始檔中隱藏項目概觀](../code-quality/in-source-suppression-overview.md)|深入瞭解 ISS，以及如何在您的程式碼中使用。|
|[如何：使用功能表項目隱藏警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)|瞭解如何 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 使用快捷方式功能表隱藏 IDE 中的警告。|

## <a name="related-sections"></a>相關章節
 [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
