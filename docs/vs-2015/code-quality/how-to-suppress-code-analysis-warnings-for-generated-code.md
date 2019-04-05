---
title: HOW TO：隱藏所產生的程式碼的程式碼分析警告 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c39ee1113d04cdd3212deccee626a96dd1e3dae7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939433"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>HOW TO：隱藏所產生程式碼的程式碼分析警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Managed 程式碼編譯器通常會產生加入至專案，以協助快速的程式碼開發的程式碼。 此外，開發人員通常會使用第三方工具來幫助您快速開發應用程式。 這些工具也會產生程式碼加入至專案。  
  
 您可能想要查看產生的程式碼可探索程式碼分析規則違規。 不過，您可能不想看到它們，如果您無法檢視，並維護包含違規的程式碼。  
  
 **隱藏所產生的程式碼的結果**專案的程式碼分析屬性頁面上的核取方塊可讓您選取您是否想要看到從協力廠商工具所產生的程式碼的程式碼分析警告。  
  
> [!NOTE]
>  此選項無法隱藏時的錯誤和警告會出現在表單和範本程式碼分析錯誤和警告，從產生的程式碼。 您可以同時檢視及維護表單或範本的原始程式碼。  
  
### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>若要隱藏的警告，請在專案中產生程式碼  
  
1.  以滑鼠右鍵按一下方案總管 中的專案，然後按一下**屬性**。  
  
2.  按一下 **程式碼分析**。  
  
3.  選取 [**隱藏所產生的程式碼的結果**] 核取方塊。
