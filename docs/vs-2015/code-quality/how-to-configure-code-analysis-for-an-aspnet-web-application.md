---
title: 如何：設定 ASP.NET Web 應用程式的程式碼分析 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 423264362118343d573b417cd055d2d722df995e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657455"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>如何：設定 ASP.NET Web 應用程式的程式碼分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在中， [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] 您可以從要套用至 Web 應用程式的程式碼分析 *規則集* 清單中選取 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 。 預設規則集是 Microsoft 最低建議的規則。 您可以選取另一個規則集以套用至網站。

### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>若要設定 ASP.NET 網頁架構專案的規則集

1. 在 [ **方案總管**中選取網站。

2. 在 [ **分析** ] 功能表上，按一下 [ **設定網站的程式碼分析**]。

3. 如果您選取解決方案，且解決方案有一個 **以上的專案** ，請從 [設定] 和 [ **平臺** ] 清單中選取組建設定和目標作業系統。

4. 針對方案中的每個專案，按一下 [ **規則集** ] 資料行，然後按一下要執行之規則集的名稱。

5. 根據預設，程式碼分析會在方案中的所有專案上執行。 若要停用或啟用特定專案的程式碼分析，請遵循下列步驟：

    1. 以滑鼠右鍵按一下專案名稱，然後按一下 [屬性]。

    2. 選取或清除 [ **啟用程式碼分析** ] 核取方塊。 您也可以在 [**分析**] 功能表中選取 [從**網站執行程式碼分析**]，手動執行程式碼分析。

6. 在 [ **執行此規則集** ] 下拉式清單中，依照下列步驟執行：

    - 選取您要使用的規則集。

    - 選取 **\<Browse>** 此項可指定不在清單中的現有自訂規則集。

    - 定義自訂規則集。 如需詳細資訊，請參閱 [建立自訂規則集](../code-quality/creating-custom-code-analysis-rule-sets.md)。
