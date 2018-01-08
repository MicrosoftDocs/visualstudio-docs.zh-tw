---
title: "選擇網域特定領域語言方案範本 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: "24"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: b636ab7937c85199c26b8ce8a95fa33cdcc7976b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>選擇網域指定的語言方案範本
若要建立特定領域語言方案中，選擇一個網域特定語言設計工具精靈 中的方案範本。 藉由選擇最接近的語言，您想要建立的範本，您可以減少您必須起始方案進行的修改。  
  
 下列解決方案範本可用於特定領域語言設計工具精靈。  
  
|範本|功能|描述|  
|--------------|--------------|-----------------|  
|類別圖表|-區間圖案<br />類別繼承<br />-關聯性繼承<br />繼承圖形<br />-關聯性屬性|如果您的特定領域語言包括實體和屬性的關聯性，請使用此解決方案範本。 此範本所建立的網域特定定義域語言類似 UML 類別圖。 主要實體是類別和介面，以及關聯、 一般化和實作的關聯性。 類別或介面顯示為方塊包含的屬性清單。|  
|元件圖表|-連接埠|如果您的特定領域語言包括元件，也就是軟體系統組件，請使用此解決方案範本。 此範本所建立的網域特定定義域語言類似 UML 元件圖表。 主要實體為元件和連接埠，會顯示為小型外部元件的形狀。|  
|工作流程圖表|-映像和幾何形狀<br />-   *泳道*|如果您的特定領域語言包含工作流程、 狀態或順序，請使用此解決方案範本。 此範本所建立的網域特定定義域語言類似 UML 活動圖表。 主要實體是活動，而且主要關聯性的活動之間的轉換。 範本包含數個其他項目例如開始狀態，最終狀態和同步處理列。|  
|最小的語言|-一個類別和形狀<br />-一的關聯性和連接器|如果您的特定領域語言不相似其他範本，請使用此解決方案範本。 此範本所建立的網域特定定義域語言具有兩個類別和一個關聯性，以表示**工具箱**為**方塊**和**列**。 類別和關聯性各有一個範例字串的屬性。|  
|最小 WinForm 設計工具|-小型的模型。<br />-顯示模型在 Windows Form。|如果您想要建置應用程式中 DSL 繫結至 Windows Form，而不是圖形化設計工具，請使用此範本。<br /><br /> 格式，可做為使用者介面語言，是 Dsl\UI 資料夾中。<br /><br /> 開啟表單設計工具之前，您應該建置專案。<br /><br /> 如需詳細資訊，請參閱[建立 Windows Forms-Based 特定領域語言](../modeling/creating-a-windows-forms-based-domain-specific-language.md)。|  
|最小的 WPF 設計工具|-小型模型<br />-顯示模型 Windows Presentation Foundation 使用者介面|如果您想要建置應用程式中 DSL 繫結至 WPF 使用者介面，而不是圖形化設計工具，請使用此範本。<br /><br /> 使用者介面的設計工具是 Dsl\UI 資料夾中。<br /><br /> 開啟 UI 設計工具之前，您應該建置專案。<br /><br /> 如需詳細資訊，請參閱[建立 WPF-Based 特定領域語言](../modeling/creating-a-wpf-based-domain-specific-language.md)。|  
|DSL 程式庫|-最小的程式庫|如果您想要建立部分的 DSL 定義可以匯入其他 DSL 定義，請使用此範本。|  
  
## <a name="see-also"></a>請參閱  
 [特定領域語言工具概觀](../modeling/overview-of-domain-specific-language-tools.md)
