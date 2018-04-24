---
title: 程式碼分析簽入原則的版本相容性
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25e8ee0bf46840d420f5537a2ca28965522dea43
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>程式碼分析簽入原則的版本相容性
如果您必須評估，並撰寫程式碼分析簽入原則使用不同版本的[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]，您必須知道的方式不同[!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)]和[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]評估簽入原則。

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>版本相容性評估簽入原則

-   程式碼分析簽入原則中的評估時[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]，存在於任何規則[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]但不是存在於[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]都會被忽略。

-   程式碼分析簽入原則中的評估時[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]，所有新的規則所專屬[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]都會被忽略。

-   如果程式碼分析簽入原則指定規則組件，[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]會忽略所有規則所指定的組件，卻無法辨識。

-   如果程式碼分析簽入原則指定規則組件的[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]無法辨識，則會顯示訊息。

## <a name="version-compatibility-for-authoring-check-in-policies"></a>撰寫簽入原則的版本相容性

-   如果您使用建立程式碼分析簽入原則[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]版本[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]，您不能使用[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]版本[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]進行修改。 請和[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]無法評估的原則。

-   如果您使用建立程式碼分析簽入原則[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]中[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]，您可以使用[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]中[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]來修改它，並將原則也可由評估[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]。 使用修改原則後[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]中[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]，您可以使用，以無法再編輯原則[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]中[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]。 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 可評估原則，而不會產生強式名稱不相符的問題。

-   若要建立程式碼分析簽入原則兩者套用的規則設定與[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]和[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]，您必須建立在原則[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]、 進行需要的所有變更並儲存原則。 如果規則的變更僅存在於[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]，您修改並儲存在原則[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]。

     當您儲存中的原則之後[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]，您無法再變更中存在的規則設定[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]只。