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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609310"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>程式碼分析簽入原則的版本相容性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您必須使用不同的版本來評估及撰寫程式碼分析簽入原則 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] ，您必須知道如何 [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] 和 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 評估簽入原則的差異。

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>評估簽入原則的版本相容性

- 在中評估程式碼分析簽入原則時 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] ， [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 會忽略存在於但不存在於中的任何規則 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 。

- 在中評估程式碼分析簽入原則時 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] ，會忽略所有專有的新規則 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 。

- 如果程式碼分析簽入原則指定規則元件， [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 則會忽略無法辨識的元件所指定的所有規則。

- 如果程式碼分析簽入原則指定無法辨識的規則元件 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] ，則會顯示一則訊息。

## <a name="version-compatibility-for-authoring-check-in-policies"></a>撰寫簽入原則的版本相容性

- 如果您使用的版本建立了程式碼分析簽入原則 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] ，您就無法使用的 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 版本 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] 來修改它。 此外，也 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 無法評估原則。

- 如果您使用中的來建立程式碼分析簽入 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] 原則 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] ，您可以使用 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] 中的 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 修改它，也可以評估原則 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 。 使用中的修改原則之後 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] ，您就無法再使用中的來編輯原則 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 。 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 可以評估原則，而不會有不相符強式名稱的問題。

- 若要使用適用于和的規則設定來建立程式碼分析簽入原則， [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 您必須在中建立原則 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 、進行所有需要的變更，然後儲存原則。 如果規則的變更只存在於中 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] ，則您可以在中修改並儲存原則 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 。

     當您在中儲存原則之後 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] ，就無法再變更僅存在之規則的設定 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 。
