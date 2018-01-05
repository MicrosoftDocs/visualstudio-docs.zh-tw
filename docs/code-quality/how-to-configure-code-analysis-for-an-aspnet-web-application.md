---
title: "如何： 設定 ASP.NET Web 應用程式的程式碼分析 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: 51ece959ad0c33c4676e81203cacc025d9ef2884
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>如何：設定 ASP.NET Web 應用程式的程式碼分析
在[!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)]和[!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)]您可以從程式碼分析的清單中選取*規則集*要套用至[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Web 應用程式。 預設規則設為 Microsoft Mininimum 建議規則。 您可以選取另一個規則集套用至網站。  
  
### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>若要設定 ASP.NET 網頁架構專案的規則集  
  
1.  選取網站中**方案總管 中**。  
  
2.  在**分析**功能表上，按一下 **設定網站的程式碼分析**。  
  
3.  如果您選取方案，方案中有多個專案選取的組建組態和目標作業系統從**組態**和**平台**列出。  
  
4.  在方案中每個專案，請按一下**規則集**資料行，然後按一下 規則名稱設定為執行。  
  
5.  根據預設，方案中的所有專案上執行的程式碼分析。 若要停用或啟用特定專案的程式碼分析，請遵循下列步驟：  
  
    1.  以滑鼠右鍵按一下專案名稱，然後按一下 屬性。  
  
    2.  請選取或清除**啟用程式碼分析**核取方塊。 您也可以執行程式碼分析手動選取**網站上執行程式碼分析**從**分析**功能表。  
  
6.  在**執行此規則集**下拉式清單中，請遵循下列步驟：  
  
    -   選取您想要使用的規則集。  
  
    -   選取**\<瀏覽 >** ，指定現有的自訂規則集不在清單中。  
  
    -   定義自訂規則集。 如需詳細資訊，請參閱[建立自訂規則集](../code-quality/creating-custom-code-analysis-rule-sets.md)。