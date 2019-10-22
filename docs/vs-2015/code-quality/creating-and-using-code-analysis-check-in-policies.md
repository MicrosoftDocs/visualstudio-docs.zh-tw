---
title: 建立和使用程式碼分析簽入原則 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8e31ff799edc93d250eeeab57b349873a63ecf14
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667718"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>建立和使用程式碼分析簽入原則
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您使用 Team Foundation 版本控制（TFVC）時，您可以為 Team 專案中的 .NET Framework 和原生（C/C++）程式碼專案建立程式碼分析簽入原則。 您可以使用程式碼分析簽入原則來控制和改善已簽入程式碼基底的程式碼品質。

 當本機組建為最新狀態，且已在最新的原始程式檔上執行程式碼分析時，原則就會通過。 在程式碼專案中啟用的程式碼分析規則，至少必須包含與 team 專案簽入原則中所定義的相同規則。 在 Team 專案設定中指定為錯誤的規則，也必須指定為程式碼專案中的錯誤

> [!IMPORTANT]
> 程式碼分析簽入原則無法套用至網站專案。 它們可以套用至 web 應用程式專案。

 您可以使用 [!INCLUDE[esprscc](../includes/esprscc-md.md)] 的 Team 專案設定來建立程式碼分析簽入原則。 系統會針對 team 專案指定和強制執行簽入原則，但會針對本機開發電腦上的個別程式碼專案設定和執行程式碼分析回合。 本節說明如何指定 team 專案的程式碼分析簽入原則，以及如何為 managed 程式碼執行自訂程式碼分析原則。

## <a name="in-this-section"></a>本章節內容
 [如何：建立或更新標準程式碼分析簽入原則](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)說明您用來設定和修改 team 專案之程式碼分析原則的步驟。

 [執行 Managed 程式碼的自訂簽入原則](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)說明您用來為 team 專案的簽入原則建立自訂規則集，以及將 team 專案的程式碼專案與簽入原則同步處理的步驟。

 程式[代碼分析簽入原則的版本相容性](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)說明 [!INCLUDE[vstsLong](../includes/vstslong-md.md)] 版本之間的程式碼分析簽入相容性問題。

 [如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)說明如何將文字和標記加入至程式碼分析命名規則中所參考的字典。

## <a name="related-sections"></a>相關章節
 [品質嚴格把關](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)

 [使用 Team 專案簽入原則強化程式碼品質](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)
