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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668343"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>選擇網域指定的語言方案範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要建立特定領域語言方案，請選擇特定領域語言設計工具 Wizard 提供的其中一個解決方案範本。 藉由選擇最接近您要建立之語言的範本，您可以將必須對起始方案所做的修改減至最少。

 特定領域語言設計工具 Wizard 提供下列解決方案範本。

> [!NOTE]
> 範本的目的是要提供起始的 DSL。 命名為 [類別] 和 [元件圖表] 的範本並非完整的 UML 圖表。 如果您想要建立 UML 模型，請考慮使用 UML 模型工具，其提供一組在單一模型周圍整合的圖表。 它們可以擴充，並且可以使用 ModelBus 與 DSL 整合。 如需詳細資訊，請參閱為 [您的應用程式建立模型](../modeling/create-models-for-your-app.md)。

|[範本]|特性|描述|
|--------------|--------------|-----------------|
|類別圖表|-區間圖形<br />-類別繼承<br />-關聯性繼承<br />-圖形繼承<br />-關聯性屬性|如果您的特定領域語言包含具有屬性的實體和關聯性，請使用此解決方案範本。 此範本會建立類似 UML 類別圖表的特定領域語言。 主要實體是類別和介面，以及關聯、一般化和執行關聯性。 類別或介面會顯示為包含屬性清單的方塊。|
|元件圖|-埠|如果您的網域特定語言包含元件，也就是軟體系統的元件，請使用此解決方案範本。 此範本會建立類似于 UML 元件圖的特定領域語言。 主要實體是元件和埠，在元件外部顯示為小圖形。|
|工作流程圖表|-影像和幾何圖形<br />-   *泳道*|如果您的特定領域語言包含工作流程、狀態或順序，請使用此解決方案範本。 此範本會建立類似于 UML 活動圖表的特定領域語言。 主要實體是一個活動，而主要的關聯性是活動之間的轉換。 此範本包含數個其他元素，例如開始狀態、最終狀態和同步處理列。|
|最小語言|-一個類別和圖形<br />-一個關聯性和連接器|如果您的網域特定語言與其他範本不相似，請使用此解決方案範本。 此範本會建立具有兩個類別和一個關聯性的網域特定語言，這些類別在 [ **工具箱** ] 中是以 **Box** 和 **Line**表示。 類別和關聯性都有範例字串屬性。|
|基本 WinForm 設計師|-小型模型。<br />-顯示模型的 Windows Form。|如果您想要建立一個應用程式，其中 DSL 系結至 Windows Form，而不是圖形化設計工具，請使用此範本。<br /><br /> 作為語言之使用者介面的表單位於資料夾 Dsl\UI。<br /><br /> 您應該先建立專案，再開啟表單設計工具。<br /><br /> 如需詳細資訊，請參閱 [建立以 Windows Forms 為基礎的特定領域語言](../modeling/creating-a-windows-forms-based-domain-specific-language.md)。|
|基本 WPF 設計工具|-小型模型<br />-顯示模型的 Windows Presentation Foundation 使用者介面|如果您想要建立一個應用程式，其中 DSL 系結至 WPF 使用者介面，而不是圖形化設計工具，請使用此範本。<br /><br /> 使用者介面的設計工具位於 Dsl\UI. 資料夾中。<br /><br /> 開啟 UI 設計工具之前，您應該先建立專案。<br /><br /> 如需詳細資訊，請參閱 [建立以 WPF 為基礎的特定領域語言](../modeling/creating-a-wpf-based-domain-specific-language.md)。|
|DSL 程式庫|-基本程式庫|如果您想要建立可匯入其他 DSL 定義的部分 DSL 定義，請使用此範本。|

## <a name="see-also"></a>另請參閱
 [Domain-Specific Language Tools 概觀](../modeling/overview-of-domain-specific-language-tools.md)
