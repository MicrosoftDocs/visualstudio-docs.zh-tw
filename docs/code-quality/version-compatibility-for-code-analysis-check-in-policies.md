---
title: 程式碼分析簽入原則的版本相容性
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c233d174922c0853d771356e0b68185c51c368ea
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448730"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>程式碼分析簽入原則的版本相容性

如果您必須使用不同版本的 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] 來評估和撰寫程式碼分析簽入原則，您必須知道 [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] 和 @no__t 2 評估簽入原則的差異。

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>評估簽入原則的版本相容性

- 在 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 中評估程式碼分析簽入原則時，會忽略存在於 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 但不存在於 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 中的任何規則。

- 在 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 中評估程式碼分析簽入原則時，會忽略 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 專有的所有新規則。

- 如果程式碼分析簽入原則指定規則元件，[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 會忽略無法辨識之元件所指定的所有規則。

- 如果程式碼分析簽入原則指定了 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 無法辨識的規則元件，則會顯示訊息。

## <a name="version-compatibility-for-authoring-check-in-policies"></a>撰寫簽入原則的版本相容性

- 如果您使用 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] 的 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 版本建立程式碼分析簽入原則，則無法使用 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] 的 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 版本來進行修改。 此外，[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 也無法評估原則。

- 如果您使用 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 中的 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] 來建立程式碼分析簽入原則，您可以使用 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 中的 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] 來修改它，而且也可以透過 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 來評估原則。 使用 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 中的 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] 修改原則之後，您就無法再使用 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 中的 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] 來編輯原則。 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 可評估原則，而不會產生強式名稱不相符的問題。

- 若要使用同時適用于 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 和 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 的規則設定來建立程式碼分析簽入原則，您必須在 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 中建立原則，進行所有必要的變更，然後儲存原則。 如果規則的變更只存在於 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]，您就可以在 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 中修改和儲存原則。

   將原則儲存在 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 之後，您就無法再變更僅存在於 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 中的規則設定。
