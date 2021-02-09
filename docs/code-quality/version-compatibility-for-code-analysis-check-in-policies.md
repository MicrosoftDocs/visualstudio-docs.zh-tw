---
title: 程式碼分析簽入原則的版本相容性
ms.date: 11/04/2016
description: 瞭解 Team System 2008 Team Foundation Server 和 Team Foundation Server 2010 如何以不同的方式評估 Visual Studio 簽入原則。
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24a97e9175e75d8018aff269066f13a796e1cf64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867668"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>程式碼分析簽入原則的版本相容性

如果您必須使用不同的版本來評估及撰寫程式碼分析簽入原則 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] ，您必須知道如何 [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] 和 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 評估簽入原則的差異。

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>評估 Check-In 原則的版本相容性

- 在中評估程式碼分析簽入原則時 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ， [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 會忽略存在於但不存在於中的任何規則 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 。

- 在中評估程式碼分析簽入原則時 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ，會忽略所有專有的新規則 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 。

- 如果程式碼分析簽入原則指定規則元件， [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 則會忽略無法辨識的元件所指定的所有規則。

- 如果程式碼分析簽入原則指定無法辨識的規則元件 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ，則會顯示一則訊息。

## <a name="version-compatibility-for-authoring-check-in-policies"></a>編寫 Check-In 原則的版本相容性

- 如果您使用的版本建立了程式碼分析簽入原則 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] ，您就無法使用的 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 版本 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] 來修改它。 此外，也 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 無法評估原則。

- 如果您使用中的來建立程式碼分析簽入 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] 原則 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ，您可以使用 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] 中的 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 修改它，也可以評估原則 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 。 使用中的修改原則之後 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ，您就無法再使用中的來編輯原則 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 。 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 可以評估原則，而不會有不相符強式名稱的問題。

- 若要使用適用于和的規則設定來建立程式碼分析簽入原則， [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 您必須在中建立原則 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 、進行所有需要的變更，然後儲存原則。 如果規則的變更只存在於中 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ，則您可以在中修改並儲存原則 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 。

   當您在中儲存原則之後 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ，就無法再變更僅存在之規則的設定 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 。
