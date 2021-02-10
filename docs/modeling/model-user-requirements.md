---
title: 模型使用者需求
description: 瞭解 Visual Studio 如何藉由繪製活動圖表來協助您瞭解、討論和溝通使用者的需求。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d55e549d2dccdc047cbf4449392cc090a569f85c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970578"
---
# <a name="model-user-requirements"></a>模型使用者需求

Visual Studio 透過繪製使用者活動的圖表，以及系統協助他們達到其目標所扮演的角色，幫助您了解、討論和溝通使用者需求。 需求模型是這些圖表的其中一組，各著重於使用者需求的不同層面。 如需視訊示範，請參閱︰ [Modeling the Business Domain](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain)(模型化商務網域)。

若要查看支援各類型之模型的 Visual Studio 版本，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

需求模型可協助您：

- 著重於系統的外部行為，與其內部設計分開。

- 使用自然語言，更明確地描述使用者和利害關係人的需求。

- 定義使用者、開發人員和測試人員可使用的一致詞彙表。

- 減少需求的缺口和不一致。

- 減少回應需求變更所需的工作。

- 規劃功能的開發順序。

- 使用模型作為進行系統測試的基礎，以設定測試與需求之間的清楚關聯性。 需求變更時，此關聯性可協助您正確地更新測試。 這可確保系統符合新的需求。

如果您使用需求模型來聚焦與使用者或其業務人員的討論，並在每次重複的開頭重新瀏覽該討論，則需求模型提供最大的好處。 撰寫程式碼之前，您不需要詳細地完成它。 局部運作的應用程式 (即使極為簡化) 通常會構成使用者需求討論的最生動基礎。 模型是彙總這些討論結果的有效方法。 如需詳細資訊，請參閱 [在開發過程中使用模型](../modeling/use-models-in-your-development-process.md)。

> [!NOTE]
> 在這些主題中，「系統」表示您正在開發的系統或應用程式。 它可能是許多軟體和硬體元件的大型集合、單一應用程式或較大系統內的軟體元件。 在每種情況下，需求模型都會描述可在系統外部看到的行為 (不論是透過使用者介面或 API)。

## <a name="common-tasks"></a>常見工作

您可以建立數個不同的使用者需求檢視。  每個檢視都提供特定類型的資訊。  建立這些檢視時，最好經常切換使用不同的檢視。 您可以從任何檢視開始。

|圖表或文件|需求模型中的描述|區段|
|-|-|-|
|概念性類別圖|用來描述需求的類型字彙；系統介面上可見的類型。||
|其他文件或工作項目|效能、安全性、可用性和可靠性準則。|[描述服務需求品質](#QoSRequirements)|
|其他文件或工作項目|非特定使用案例的特定條件約束和規則|[顯示商務規則](#BusinessRules)|

請注意，大部分的圖表類型都可以用於其他用途。 如需圖表類型的總覽，請參閱為 [您的應用程式建立模型](../modeling/create-models-for-your-app.md)。

## <a name="showing-business-rules"></a><a name="BusinessRules"></a> 顯示商務規則

商務規則是未與特定使用案例相關聯的需求，而且應該會在系統中觀察到。

許多商務規則是概念性類別間之關聯性的條件約束。 您可以撰寫這些 *靜態商務規則* ，作為與概念類別圖上相關類別相關聯的批註。 例如：

![附加至 Order 類別之註解的規則。](../modeling/media/uml_reqmcd2.png)

*「動態商務規則」* (dynamic business rules) 限制允許的事件序列。 例如，您可以使用序列或活動圖來示範使用者必須先登入，才能對系統執行其他作業。

不過，許多動態規則在取代為靜態規則之後會較為有效。 例如，您可以將布林值屬性 'Logged In' 加入概念性類別模型中的類別。 您將 Logged In 加入為登入使用案例中的後置條件，並將它加入為其他大部分使用案例的前置條件。 這種方法可讓您避免定義所有可能的事件序列組合。 需要將新的使用案例加入模型時，它也更有彈性。

請注意，這裡的選擇是有關如何定義需求，而且這與如何在程式碼中實作需求無關。

下列主題提供詳細資訊：

|深入了解|讀取|
|-|-|
|如何開發遵守商務規則的程式碼|[建立應用程式架構的模型](../modeling/model-your-app-s-architecture.md)|

## <a name="describing-quality-of-service-requirements"></a><a name="QoSRequirements"></a> Describing Quality of Service Requirements

有數種類別的服務需求品質。 其包括：

- 效能

- 安全性

- 可用性

- 可靠性

- 加強性

您可以在特定使用案例描述中包含其中一些需求。 其他需求非使用案例所特定，而且最有效地撰寫於不同的文件中。 如果可以，最好遵守需求模型所定義的詞彙。 在下列範例中，請注意，要求中所使用的主要單字是先前圖例中的行動標題、使用案例和類別：

如果餐廳刪除「菜單項目」(Menu Item) 時，客人正在點餐，則會以紅色顯示參照該「菜單項目」(Menu Item) 的任何「訂單項目」(Order Item)。

請參閱 [模型應用程式架構](../modeling/model-your-app-s-architecture.md) ，以瞭解如何開發符合服務需求品質的程式碼。

## <a name="see-also"></a>另請參閱

- [在開發程序中使用模型](../modeling/use-models-in-your-development-process.md)
- [建立應用程式架構的模型](../modeling/model-your-app-s-architecture.md)
