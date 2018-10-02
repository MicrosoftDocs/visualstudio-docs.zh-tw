---
title: 如何： 設定 Managed 程式碼專案的程式碼分析 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 34c3088aee4089c69669eaa3af5a08a657553363
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499975"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>如何：設定 Managed 程式碼專案的程式碼分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 設定 Managed 程式碼專案的程式碼分析](https://docs.microsoft.com/visualstudio/code-quality/how-to-configure-code-analysis-for-a-managed-code-project)。  
  
在[!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]，[!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]並[!INCLUDE[vsPro](../includes/vspro-md.md)]，您可以從程式碼分析的清單中選擇*規則集*来套用至 managed 程式碼專案。 預設規則設為 Microsoft 最小建議規則。 您可以套用設定至專案或方案中的所有專案的另一個規則。  
  
> [!NOTE]
>  如需如何設定 ASP.NET Web 應用程式設定的規則資訊，請參閱[如何： 設定 ASP.NET Web 應用程式的程式碼分析](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)。  
  
### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>若要設定的規則集的.NET Framework 專案  
  
1.  在 [**方案總管] 中**，按一下 [專案]。  
  
2.  在上**分析**功能表上，按一下**設定的程式碼分析** *ProjectName*。  
  
3.  在 **組態**並**平台**清單中，按一下 組建組態和目標平台。  
  
4.  若要執行程式碼分析，每次使用選取的組態建置專案時，請選取**啟用建置程式碼分析 （定義 CODE_ANALYSIS 常數）** 核取方塊。 您也可以執行程式碼分析手動開啟**分析**功能表，然後按一下**上執行程式碼分析** *ProjectName*。  
  
5.  根據預設，程式碼分析不會報告從外部工具自動產生的程式碼警告。 若要檢視產生程式碼的警告，請清除**隱藏所產生的程式碼的結果** 核取方塊。  
  
    > [!NOTE]
    >  這個選項不會在表單和範本中出現錯誤和警告時，抑制來自產生的程式碼的程式碼分析錯誤和警告。 您可以同時檢視及維護表單或範本的原始程式碼。  
  
6.  在 **執行此規則集**清單中，執行下列其中之一：  
  
    -   按一下您想要使用的規則集。  
  
    -   按一下 [ **\<瀏覽] >** ，指定現有的自訂規則集不在清單中。  
  
    -   定義自訂規則集。  
  
         如需詳細資訊，請參閱 <<c0> [ 建立自訂規則集](../code-quality/creating-custom-code-analysis-rule-sets.md)。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：設定和使用自訂規則集](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)



