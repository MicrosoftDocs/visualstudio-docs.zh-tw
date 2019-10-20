---
title: 程式碼分析簽入原則的版本相容性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 075981569cbee05e90afe17b3afc9558d7bbb270
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609310"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>程式碼分析簽入原則的版本相容性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您必須使用不同的 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] 版本來評估和撰寫程式碼分析簽入原則，您必須知道 [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] 和 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 評估簽入原則的方式差異。

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>評估簽入原則的版本相容性

- 在 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 中評估程式碼分析簽入原則時，會忽略存在於 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 但不存在於 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 中的任何規則。

- 在 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 中評估程式碼分析簽入原則時，會忽略 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 獨有的所有新規則。

- 如果程式碼分析簽入原則指定規則元件，[!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 會忽略無法辨識之元件所指定的所有規則。

- 如果程式碼分析簽入原則指定 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 無法辨識的規則元件，則會顯示訊息。

## <a name="version-compatibility-for-authoring-check-in-policies"></a>撰寫簽入原則的版本相容性

- 如果您使用 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] 的 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 版本來建立程式碼分析簽入原則，就無法使用 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] 的 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 版本來進行修改。 此外，[!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 無法評估原則。

- 如果您使用 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 中的 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] 來建立程式碼分析簽入原則，您可以在 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 中使用 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] 來進行修改，而且也可以藉由 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 評估該原則。 使用 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 中的 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] 修改原則之後，您就無法再使用 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 中的 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] 來編輯原則。 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 可評估原則，而不會產生強式名稱不相符的問題。

- 若要使用同時適用于 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 和 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 的規則設定來建立程式碼分析簽入原則，您必須在 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 中建立原則、進行所需的所有變更，然後儲存原則。 如果規則的變更只存在於 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 中，您會在 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 中修改和儲存原則。

     在 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 中儲存原則之後，就無法再變更僅存在於 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 中的規則設定。
