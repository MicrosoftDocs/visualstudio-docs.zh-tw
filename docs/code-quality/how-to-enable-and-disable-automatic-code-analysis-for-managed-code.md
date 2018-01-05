---
title: "如何： 啟用和停用自動程式碼分析，Managed 程式碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c22d194-5fea-4f23-b02d-19344fa64a64
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 198047196ba6f58c69736ef67352267845047b52
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>如何：啟用和停用 Managed 程式碼的自動程式碼分析
您可以設定每個 managed 程式碼專案的組建之前執行的程式碼分析。 您可以設定不同的程式碼分析屬性，每個[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]組態。  
  
### <a name="to-enable-or-disable-automatic-code-analysis"></a>若要啟用或停用自動程式碼分析  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下專案，然後按一下**屬性**。  
  
2.  在專案屬性對話方塊、 按一下**程式碼分析**。  
  
3.  指定組建類型中的**組態**與目標平台的**平台**。  
  
4.  若要啟用或停用自動程式碼分析，請選取或清除**啟用建置程式碼分析 （定義 CODE_ANALYSIS 常數）**核取方塊。