---
title: 選擇網域指定的語言方案範本
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b76b61bb0ff84d3e1f0948057b60f6f3fbb505ad
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590562"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>選擇網域指定的語言方案範本
若要建立特定領域語言方案，請選擇 [網域指定的語言設計工具] 中提供的其中一個方案範本。 藉由選擇與您要建立之語言最相似的範本，您可以將必須對起始解決方案進行的修改降至最低。

 下列解決方案範本可在特定領域語言設計工具 Wizard 中使用。

|範本|功能|描述|
|-|-|-|
|類別圖表|-區間圖形<br />-類別繼承<br />-關聯性繼承<br />-圖形繼承<br />-關聯性屬性|如果您的網域特定語言包含具有屬性的實體和關聯性，請使用此解決方案範本。 此範本會建立類似 UML 類別圖表的特定領域語言。 主要實體為類別和介面，以及關聯、一般化和實關係。 類別或介面會顯示為包含屬性清單的方塊。|
|元件圖|-埠|如果您的特定領域語言包含元件（也就是軟體系統的一部分），請使用此解決方案範本。 此範本會建立類似 UML 元件圖表的特定領域語言。 主要實體是元件和埠，會在元件外部顯示為小型圖形。|
|工作流程圖|-影像和幾何圖形<br />-   *泳道*|如果您的特定領域語言包含工作流程、狀態或順序，請使用此解決方案範本。 此範本會建立類似 UML 活動圖的特定領域語言。 主要實體是活動，而主要關聯性則是活動之間的轉換。 此範本包含其他幾個專案，例如啟動狀態、最終狀態和同步處理列。|
|最小語言|-一個類別和圖形<br />-一個關聯性和連接器|如果您的網域特定語言與其他範本不相似，請使用此解決方案範本。 此範本會建立有兩個類別和一個關聯性的特定領域語言，在 [**工具箱**] 中表示為 [ **Box** ] 和 [**線條**]。 類別和關聯性各有一個範例字串屬性。|
|最基本的 WinForm 設計工具|-小型模型。<br />-顯示模型的 Windows Form。|如果您想要建立一個應用程式，其中的 DSL 系結至 Windows Form，而不是圖形化設計工具，請使用此範本。<br /><br /> 作為語言使用者介面的表單位於資料夾 Dsl\UI. 中<br /><br /> 您應該先建立專案，然後再開啟表單設計工具。<br /><br /> 如需詳細資訊，請參閱[建立以 Windows Forms 為基礎的網域特定語言](../modeling/creating-a-windows-forms-based-domain-specific-language.md)。|
|最小 WPF 設計工具|-小型模型<br />-顯示模型的 Windows Presentation Foundation 使用者介面|如果您想要建立一個應用程式，其中的 DSL 系結至 WPF 使用者介面，而不是圖形化設計工具，請使用此範本。<br /><br /> 使用者介面的設計工具位於資料夾 Dsl\UI. 中<br /><br /> 您應該先建立專案，然後再開啟 UI 設計工具。<br /><br /> 如需詳細資訊，請參閱[建立以 WPF 為基礎的特定領域語言](../modeling/creating-a-wpf-based-domain-specific-language.md)。|
|DSL 程式庫|-最小程式庫|如果您想要建立可匯入至其他 DSL 定義的部分 DSL 定義，請使用此範本。|

## <a name="see-also"></a>請參閱

- [特定領域語言工具概觀](../modeling/overview-of-domain-specific-language-tools.md)
