---
title: 如何：使用功能表項目隱藏警告 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96b7433ff4f696989142aa2c2ce47982006b93b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610019"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>如何：使用功能表項目隱藏警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

注意]
> 在來源隱藏中，網站專案不支援。

 您可以使用 [程式碼分析] 視窗來隱藏程式碼分析警告。 隱藏警告與停用它的方式不同。 當您隱藏警告時，它只會套用到違規的特定實例。 相同警告的其他違規仍然會在錯誤清單視窗中回報。

 執行程式碼分析之後，您可能會判斷 [程式碼分析] 視窗中顯示的一或多個程式碼分析警告，不適用於您的應用程式。 例如，您可能會判斷程式碼是否正確無誤。 或者，可能是某些違規是低優先順序的情況，而且不會在目前的開發週期中修正。 不論原因為何，指出警告不適用，讓您的小組成員知道程式碼已經過審核，並判定警告可能會被抑制。 在來源隱藏中很有用，因為它可讓您將隱藏專案靠近產生警告的位置。

 您可以選擇是否要在原始程式碼或全域隱藏專案檔案中顯示隱藏專案。 某些隱藏專案必須放在全域隱藏專案檔案中。 如果是這種情況，將會停用 [**在來源中**] 選項。

### <a name="to-suppress-a-warning-by-using-menu-item"></a>使用功能表項目隱藏警告

1. 在 [**分析**] 功能表上，選擇 [ **Windows** ]，然後選擇 [程式**代碼分析**]。

2. 在 [程式**代碼分析**] 視窗中，選取警告 [隱藏]。

3. 選擇 [動作]，然後選擇 [**隱藏訊息**]，然後在 [**來源**] 或 [**專案隱藏**檔] 中選擇。

     會隱藏特定的警告，而且會在 [程式碼分析] 視窗中顯示具有刪除線的警告。

> [!NOTE]
> 沒有目標的隱藏專案會出現在全域隱藏專案檔案中。
