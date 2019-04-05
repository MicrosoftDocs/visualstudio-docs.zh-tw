---
title: HOW TO：設定 ASP.NET Web 應用程式的程式碼分析 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 67cfc63c74755b10d7b3d274c0925d83b9a2d24c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940127"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>HOW TO：設定 ASP.NET Web 應用程式的程式碼分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)]及[!INCLUDE[vsUltShort](../includes/vsultshort-md.md)]您可以從程式碼分析的清單中選取*規則集*要套用至[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Web 應用程式。 預設規則設為 Microsoft Mininimum 建議規則。 您可以選取要套用至網站所設定的另一個規則。  
  
### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>若要設定 ASP.NET 網頁架構專案的規則集  
  
1.  選取網站中**方案總管 中**。  
  
2.  在 **分析**功能表上，按一下**設定網站的程式碼分析**。  
  
3.  如果您選取的方案，方案中有一個以上的專案，請選取組建組態和目標的作業系統從**組態**並**平台**列出。  
  
4.  在方案中每個專案，請按一下**規則集**資料行，然後按一下 規則名稱設為執行。  
  
5.  根據預設，方案中的所有專案上執行的程式碼分析。 若要停用或啟用特定專案的程式碼分析，請遵循下列步驟：  
  
    1.  以滑鼠右鍵按一下專案名稱，然後按一下 屬性。  
  
    2.  請選取或清除**啟用程式碼分析**核取方塊。 您也可以執行程式碼分析以手動方式選取**網站上執行程式碼分析**從**分析**功能表。  
  
6.  在 **執行此規則集**下拉式清單中，請遵循下列步驟：  
  
    -   選取您想要使用的規則集。  
  
    -   選取  **\<瀏覽 >** ，指定現有的自訂規則集不在清單中。  
  
    -   定義自訂規則集。 如需詳細資訊，請參閱 <<c0> [ 建立自訂規則集](../code-quality/creating-custom-code-analysis-rule-sets.md)。
