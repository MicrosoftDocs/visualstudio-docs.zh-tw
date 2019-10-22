---
title: 如何：隱藏所產生程式碼的程式碼分析警告 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 52caadd7f4dd9349eccb80a366a1458212aba5ca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646267"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>如何：隱藏所產生程式碼的程式碼分析警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Managed 程式碼編譯器通常會產生新增至專案的程式碼，以加快程式碼開發的速度。 此外，開發人員通常會使用協力廠商工具來協助快速開發應用程式。 這些工具也會產生新增至專案的程式碼。

 您可能想要查看程式碼分析在產生的程式碼中探索到的規則違規。 不過，如果您無法查看和維護包含違規的程式碼，則可能不會想要查看它們。

 專案的 [程式碼分析] 屬性頁上的 [**隱藏產生的程式碼的結果**] 核取方塊可讓您選取是否要從協力廠商工具產生的程式碼中查看程式碼分析警告。

> [!NOTE]
> 當表單和範本中出現錯誤和警告時，這個選項不會抑制產生的程式碼中的程式碼分析錯誤和警告。 您可以同時檢視及維護表單或範本的原始程式碼。

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>若要隱藏專案中產生之程式碼的警告

1. 以滑鼠右鍵按一下方案總管中的專案，然後按一下 [**屬性**]。

2. 按一下 [程式**代碼分析**]。

3. 選取 [**隱藏產生的程式碼的結果**] 核取方塊。
