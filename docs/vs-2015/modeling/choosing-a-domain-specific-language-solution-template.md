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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6522e3a1ad10f221f0ed7fc1761559ee9bc3f9b9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668343"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>選擇網域指定的語言方案範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要建立特定領域語言方案，請選擇 [網域指定的語言設計工具] 中提供的其中一個方案範本。 藉由選擇與您要建立之語言最相似的範本，您可以將必須對起始解決方案進行的修改降至最低。

 下列解決方案範本可在特定領域語言設計工具 Wizard 中使用。

> [!NOTE]
> 範本的目的是提供起始 DSL。 名為 [類別] 和 [元件圖] 的範本不是完整的 UML 圖表。 如果您想要建立 UML 模型，請考慮使用 UML 模型工具，這會提供一組在單一模型周圍整合的圖表。 它們可以擴充，並且可以使用 ModelBus 與 DSL 整合。 如需詳細資訊，請參閱為[您的應用程式建立模型](../modeling/create-models-for-your-app.md)。

|範本|功能|描述|
|--------------|--------------|-----------------|
|類別圖表|-區間圖形<br />-類別繼承<br />-關聯性繼承<br />-圖形繼承<br />-關聯性屬性|如果您的網域特定語言包含具有屬性的實體和關聯性，請使用此解決方案範本。 此範本會建立類似 UML 類別圖表的特定領域語言。 主要實體為類別和介面，以及關聯、一般化和實關係。 類別或介面會顯示為包含屬性清單的方塊。|
|元件圖|-埠|如果您的特定領域語言包含元件（也就是軟體系統的一部分），請使用此解決方案範本。 此範本會建立類似 UML 元件圖表的特定領域語言。 主要實體是元件和埠，會在元件外部顯示為小型圖形。|
|工作流程圖|-影像和幾何圖形<br />-   *泳道*|如果您的特定領域語言包含工作流程、狀態或順序，請使用此解決方案範本。 此範本會建立類似 UML 活動圖的特定領域語言。 主要實體是活動，而主要關聯性則是活動之間的轉換。 此範本包含其他幾個專案，例如啟動狀態、最終狀態和同步處理列。|
|最小語言|-一個類別和圖形<br />-一個關聯性和連接器|如果您的網域特定語言與其他範本不相似，請使用此解決方案範本。 此範本會建立有兩個類別和一個關聯性的特定領域語言，在 [**工具箱**] 中表示為 [ **Box** ] 和 [**線條**]。 類別和關聯性各有一個範例字串屬性。|
|最基本的 WinForm 設計工具|-小型模型。<br />-顯示模型的 Windows Form。|如果您想要建立一個應用程式，其中的 DSL 系結至 Windows Form，而不是圖形化設計工具，請使用此範本。<br /><br /> 作為語言使用者介面的表單位於資料夾 Dsl\UI. 中<br /><br /> 您應該先建立專案，然後再開啟表單設計工具。<br /><br /> 如需詳細資訊，請參閱[建立以 Windows Forms 為基礎的網域特定語言](../modeling/creating-a-windows-forms-based-domain-specific-language.md)。|
|最小 WPF 設計工具|-小型模型<br />-顯示模型的 Windows Presentation Foundation 使用者介面|如果您想要建立一個應用程式，其中的 DSL 系結至 WPF 使用者介面，而不是圖形化設計工具，請使用此範本。<br /><br /> 使用者介面的設計工具位於資料夾 Dsl\UI. 中<br /><br /> 您應該先建立專案，然後再開啟 UI 設計工具。<br /><br /> 如需詳細資訊，請參閱[建立以 WPF 為基礎的特定領域語言](../modeling/creating-a-wpf-based-domain-specific-language.md)。|
|DSL 程式庫|-最小程式庫|如果您想要建立可匯入至其他 DSL 定義的部分 DSL 定義，請使用此範本。|

## <a name="see-also"></a>請參閱
 [特定領域語言工具概觀](../modeling/overview-of-domain-specific-language-tools.md)
