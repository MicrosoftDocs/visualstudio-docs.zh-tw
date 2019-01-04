---
title: 設定 ASP.NET Web 應用程式的程式碼分析
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: a781e918a925ebd43110339e03d528a4cf6b3c70
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853027"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>HOW TO：設定 ASP.NET Web 應用程式的程式碼分析

在 Visual Studio 中，您可以從清單中選取的程式碼分析*規則集*要套用至[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]web 應用程式。 預設規則設為 Microsoft 最小建議規則。 您可以選取要套用至網站所設定的另一個規則。

1. 選取網站中**方案總管 中**。

2. 在 **分析**功能表上，按一下**設定網站的程式碼分析**。

3. 如果您選取的方案，方案中有一個以上的專案，請選取組建組態和目標的作業系統從**組態**並**平台**列出。

4. 在方案中每個專案，請按一下**規則集**資料行，然後按一下 規則名稱設為執行。

5. 根據預設，方案中的所有專案上執行的程式碼分析。 若要停用或啟用特定專案的程式碼分析，請遵循下列步驟：

    1. 以滑鼠右鍵按一下專案名稱，然後按一下 屬性。

    2. 請選取或清除**啟用程式碼分析**核取方塊。 您也可以執行程式碼分析以手動方式選取**網站上執行程式碼分析**從**分析**功能表。

6. 在 **執行此規則集**下拉式清單中，請遵循下列步驟：

    - 選取您想要使用的規則集。

    - 選取  **\<瀏覽 >** ，指定現有的自訂規則集不在清單中。

    - 定義[自訂規則集](../code-quality/how-to-create-a-custom-rule-set.md)。