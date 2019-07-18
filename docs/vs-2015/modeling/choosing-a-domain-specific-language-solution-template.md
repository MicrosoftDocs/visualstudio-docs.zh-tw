---
title: 選擇特定領域語言方案範本 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 36b821219b02fa77171d89214d8cf4813ce92303
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433393"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>選擇網域指定的語言方案範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要建立特定領域語言方案，選擇其中一個特定領域語言設計工具精靈 中提供的解決方案範本。 藉由選擇最接近的語言，您想要建立的範本，您可以減少的修改，您必須先啟動解決方案。  
  
 下列解決方案範本可在特定領域語言設計工具精靈。  
  
> [!NOTE]
> 範本的目的是提供開始的 DSL。 名為類別和元件圖表的範本不完整的 UML 圖表。 如果您想要建立 UML 模型，請考慮的 UML 模型工具，提供一組整合在單一模型周圍的圖表。 它們可以擴充，並且可以使用 ModelBus 與 DSL 整合。 如需詳細資訊，請參閱 <<c0> [ 建立應用程式模型](../modeling/create-models-for-your-app.md)。  
  
|範本|功能|描述|  
|--------------|--------------|-----------------|  
|類別圖表|-區間圖形<br />類別繼承<br />-關聯性繼承<br />圖形繼承<br />-關聯性屬性|如果您的特定領域語言包含實體和關聯性具有屬性，請使用此解決方案範本。 此範本會建立特定領域語言類似於 UML 類別圖。 主要實體是類別和介面，以及關聯、 一般化和實作的關聯性。 類別或介面會顯示為包含的屬性清單的方塊。|  
|元件圖表|-連接埠|如果您的特定領域語言包含元件，也就是軟體系統的組件，請使用此解決方案範本。 此範本會建立特定領域語言類似於 UML 元件圖。 主要實體是元件和連接埠，如下所示的外部元件上的小圖形。|  
|工作流程圖表|-映像和幾何形狀<br />-   *區隔線*|如果您的特定領域語言包含工作流程、 狀態或順序，請使用此解決方案範本。 此範本會建立特定領域語言類似於 UML 活動圖表。 主要實體是活動，且主要的關聯性是活動之間的轉換。 此範本包括例如開始狀態，最終狀態，並同步處理列的數個項目。|  
|最小語言|-一類別和圖形<br />-一的關聯性和連接器|如果您的特定領域語言不像其他範本，請使用此解決方案範本。 此範本會建立具有兩個類別和一個關聯性，這表示在特定領域語言**工具箱**作為**方塊**並**列**。 類別和關聯性各有一個範例字串屬性。|  
|最小 WinForm 設計工具|-A 小型的模型。<br />-顯示模型 Windows 表單。|如果您想要建置應用程式中的 DSL 繫結至 Windows 表單，而不是圖形化設計工具，請使用此範本。<br /><br /> Dsl\UI 資料夾中，不做為語言的使用者介面的表單。<br /><br /> 您應該開啟的表單設計工具之前建置專案。<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 建立 Windows Forms-Based Domain-specific Language](../modeling/creating-a-windows-forms-based-domain-specific-language.md)。|  
|最小 WPF 設計工具|-A 小型的模型<br />-顯示模型 Windows Presentation Foundation 使用者介面|如果您想要建置應用程式中的 DSL 繫結 WPF 使用者介面，而不是圖形化設計工具，請使用此範本。<br /><br /> 使用者介面的設計工具是 Dsl\UI 資料夾中。<br /><br /> 開啟 UI 設計工具之前，您應該建置專案。<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 建立 WPF-Based Domain-specific Language](../modeling/creating-a-wpf-based-domain-specific-language.md)。|  
|DSL 程式庫|-最小的程式庫|如果您想要建立部分的 DSL 定義，可以匯入其他 DSL 定義，請使用此範本。|  
  
## <a name="see-also"></a>另請參閱  
 [特定領域語言工具概觀](../modeling/overview-of-domain-specific-language-tools.md)
