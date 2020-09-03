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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72610019"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>如何：使用功能表項目隱藏警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

注意]
> 在來源隱藏專案中，不支援網站專案。

 您可以使用 [程式碼分析] 視窗來隱藏程式碼分析警告。 隱藏警告與停用警告不同。 當您隱藏警告時，它只會套用到違規的特定實例。 在 [錯誤清單] 視窗中，仍會報告其他違反相同警告的情況。

 在您執行程式碼分析之後，您可能會判斷 [程式碼分析] 視窗中顯示的一個或多個程式碼分析警告不適用您的應用程式。 例如，您可能會判斷程式碼是否正確無誤。 或者，在目前的開發週期中，可能會發生一些違規的情況，並不會加以修正。 無論原因為何，表示警告不適用，這通常很有用，可讓您的小組成員知道程式碼已經過審核，而且判斷出警告可以隱藏起來。 在 [來源隱藏] 中很有用，因為它可讓您放置接近警告產生位置的隱藏專案。

 您可以選擇隱藏專案將出現在原始程式碼中，還是顯示在全域隱藏檔中。 某些隱藏專案必須放在全域隱藏專案檔中。 如果是這種情況，則會停用 [ **In Source** ] （來源）選項。

### <a name="to-suppress-a-warning-by-using-menu-item"></a>使用功能表項目隱藏警告

1. 在 [ **分析** ] 功能表上，選擇 [ **視窗** ]，然後選擇 [程式 **代碼分析**]。

2. 在 [程式 **代碼分析** ] 視窗中，選取警告抑制。

3. 選擇 [動作]，然後選擇 [ **隱藏訊息 (s]) **，然後選擇 [ **來源** ] 或 [ **專案隱藏**檔] 檔案中的 []。

     特定警告會被隱藏，而警告會出現在 [程式碼分析] 視窗中，並顯示刪除線。

> [!NOTE]
> 沒有目標的隱藏專案會出現在全域隱藏專案檔中。
