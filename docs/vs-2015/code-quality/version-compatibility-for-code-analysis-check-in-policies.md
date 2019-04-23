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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0a63ead03baffaa0ce8047220ff1ce8a33c88be8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082226"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>程式碼分析簽入原則的版本相容性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您必須評估並撰寫程式碼分析簽入原則使用不同版本[!INCLUDE[esprtfc](../includes/esprtfc-md.md)]，您必須知道的方式不同[!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)]和[!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]評估簽入原則。  
  
## <a name="version-compatibility-for-evaluating-check-in-policies"></a>版本相容性評估簽入原則  
  
- 程式碼分析簽入原則中的評估時[!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]，存在於任何規則[!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]但不是存在於[!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]都會被忽略。  
  
- 程式碼分析簽入原則中的評估時[!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]，所有新的規則，專屬於[!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]都會被忽略。  
  
- 如果程式碼分析簽入原則指定規則組件，[!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]會忽略所有的規則所指定的組件，它無法辨識。  
  
- 如果程式碼分析簽入原則會指定規則組件，[!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]無法辨識，則會顯示訊息。  
  
## <a name="version-compatibility-for-authoring-check-in-policies"></a>撰寫簽入原則的版本相容性  
  
- 如果您使用建立程式碼分析簽入原則[!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]新版[!INCLUDE[esprtfc](../includes/esprtfc-md.md)]，您無法使用[!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]版本[!INCLUDE[esprtfc](../includes/esprtfc-md.md)]進行修改。 此外，[!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]無法評估原則。  
  
- 如果您使用建立程式碼分析簽入原則[!INCLUDE[esprtfc](../includes/esprtfc-md.md)]中[!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]，您可以使用[!INCLUDE[esprtfc](../includes/esprtfc-md.md)]中[!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]來修改它，並將原則也可透過評估[!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]。 使用修改原則之後[!INCLUDE[esprtfc](../includes/esprtfc-md.md)]中[!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]，您可以使用，以無法再編輯原則[!INCLUDE[esprtfc](../includes/esprtfc-md.md)]在[!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]。 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 可評估原則，而不會產生強式名稱不相符的問題。  
  
- 若要建立程式碼分析簽入原則規則的設定，適用於兩者[!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]並[!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]，您必須建立在原則[!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]、 進行需要的所有變更並儲存原則。 如果規則的變更僅存在於[!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]，您修改並儲存在原則[!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]。  
  
     儲存中的原則之後[!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]，您無法再變更中存在的規則設定[!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]只。
