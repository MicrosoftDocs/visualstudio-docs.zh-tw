---
title: 在開發程序中使用模型
description: 瞭解在 Visual Studio 中，您可以使用模型來協助您瞭解及變更系統、應用程式或元件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, using models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dbc817ca7bdf08c4e5ceee79a1e1113b4dd26e0c
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361426"
---
# <a name="use-models-in-your-development-process"></a>在開發程序中使用模型

在 Visual Studio 中，您可以使用模型來協助您了解並變更系統、應用程式或元件。 模型可以協助您將系統運作的領域視覺化、釐清使用者的需求、定義系統的架構、分析程式碼，以及確定您的程式碼符合需求。 請參閱 [Channel 9 影片：透過模型改進架構](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling)。

若要查看支援各類型之模型的 Visual Studio 版本，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

模型可以藉由許多方式協助您：

- 繪製模型圖表可以協助您釐清涉及需求、架構及高階設計的概念。 如需詳細資訊，請參閱 [模型使用者需求](../modeling/model-user-requirements.md)。

- 使用模型可以協助您顯示出需求中的不一致。

- 透過模型傳達可以協助您傳遞重要的概念，這比使用自然語言傳達更清楚。 如需詳細資訊，請參閱 [模型您的應用程式架構](../modeling/model-your-app-s-architecture.md)。

- 您可以偶爾使用模型來產生程式碼或其他成品，例如資料庫結構描述或文件。 例如，模型的 Visual Studio 模型元件會從模型產生。 如需詳細資訊，請參閱 [從模型產生和設定您的應用程式](../modeling/generate-and-configure-your-app-from-models.md)。

您可以在各種不同的程序中使用模型，不論是極端敏捷式還是高度形式化都可以。

## <a name="use-models-to-reduce-ambiguity"></a>使用模型來減少不明確

模組化語言會比自然語言更清楚，而且它是設計來表達軟體開發過程中通常需要的想法。

如果您的專案具有遵循敏捷式作法的小組，就可以使用模型來協助您釐清使用者劇本。 與客戶討論他們的需求時，比起撰寫特殊圖文集或原型程式碼，建立模型可以在該產品之更廣泛的區域上更快產生有用的問題。

如果您的專案很龐大，而且包含分佈於全球不同地點的小組，就可以使用模型來協助傳達需求和架構，這比使用純文字更有效率。

在這兩種情況下，建立模型幾乎總是會大幅減少不一致和語意模糊之處。 不同的專案關係人通常對於該系統運作的企業界具有不同的理解，而不同的開發人員通常對於該系統的運作方式具有不同的理解。 使用模型做為討論的焦點通常會顯示出這些差異。 如需如何使用模型來減少不一致的詳細資訊，請參閱 [模型使用者需求](../modeling/model-user-requirements.md)。

## <a name="use-models-with-other-artifacts"></a>使用模型與其他成品

模型本身並非需求規格或架構。 雖然它是用來針對這些事情更清楚地表達某些層面的工具，不過並無法表達軟體設計期間所需的所有概念。 因此，這些模型應該與其他通訊方式一起使用，例如 OneNote 頁面或段落、Microsoft Office 檔、Team Foundation 中的工作專案，或專案室牆上的附注。 除了最後一個項目以外，上述所有物件類型都可以連結至該模型的項目部分。

通常與模型一起使用的其他規格層面包含下列項目。 根據您的專案規模和樣式，可能會使用其中許多層面，或完全不使用任何層面：

- 使用者劇本。 使用者劇本是系統行為之某個層面的簡短描述 (與使用者和其他專案關係人一起討論)，該層面將在其中一個專案反覆項目中傳遞。 一般使用者案例會開始「客戶將能夠 ...」。使用者案例可能會引進一組使用案例，或者可以定義先前已開發之使用案例的延伸模組。 定義或擴充使用案例有助於讓使用者劇本更加清楚。

- 變更要求。 較正式專案中的變更要求和敏捷式專案中的使用者劇本相當類似。 敏捷式方法會將所有需求視為已在先前反覆項目中開發的項目。

- 使用案例描述。 使用案例代表使用者與系統互動來達成特定目標的其中一種方式。 完整描述包含目標、事件的主要和替代順序，以及例外結果。 使用案例圖有助於摘要說明並提供使用案例的概觀。

- 情節。 情節是一系列事件之相當詳細的描述，其中顯示系統、使用者和其他系統如何一起運作，提供給專案關係人價值。 它可能會採用使用者介面之投影片放映或使用者介面原型的形式。 它可以描述單一使用案例或一系列使用案例。

- 字彙。 專案的需求字彙可描述客戶用來討論其領域的單字。 使用者介面和需求模型應該也會使用這些詞彙。 類別圖可以協助釐清大部分詞彙之間的關聯性。 建立此圖表和字彙不僅可減少使用者與開發人員之間的誤解，而且也幾乎總是能顯示出不同商務專案關係人之間的誤解。

- 商務規則。 許多商務規則都可以表達成需求類別模型中關聯和屬性的非變異條件約束，以及表達成循序圖的條件約束。

- 高階設計。 描述這主要的部分以及它們如何相互配合。 元件、順序和介面圖表是高階設計的主要部分。

- 設計模式。 描述在該系統不同部分之間共用的設計規則。

- 測試規格。 測試指令碼和測試程式碼的設計可以充分運用活動和循序圖來描述測試步驟的順序。 您應該根據需求模型表達系統測試，以便在需求變更時更輕易地變更系統測試。

- 專案計劃。 專案計劃或待處理項目會定義何時要傳遞每項功能。 您可以指出每項功能所實作或擴充的使用案例和商務規則，藉以定義每項功能。 您可以直接在計劃中參考使用案例和商務規則，或是在個別的文件中定義一組功能，然後在該計劃中使用此功能標題。

## <a name="use-models-in-iteration-planning"></a>在反復專案計劃中使用模型

雖然所有專案的規模和組織都不同，不過一般專案會規劃成介於二至六週的一系列反覆項目。 請務必規劃足夠的反覆項目，以便利用早期反覆項目的意見回應來調整後期反覆項目的範圍和計劃。

您可能會發現下列建議事項有助於實現在反覆式專案中使用模型的益處。

### <a name="sharpen-focus-as-each-iteration-approaches"></a>在每個反復專案方法中將焦點銳化

在每個反覆項目進行時，使用模型來協助定義該反覆項目結束時所傳遞的項目。

- 請勿在早期的反覆項目中詳細模型化所有項目。 在第一個反覆項目中，請針對使用者字彙中的主要項目建立類別圖、繪製主要使用案例的圖表，並且繪製主要元件的圖表。 請勿詳細描述其中任何項目，因為這個詳細資料之後將在專案中變更。 使用這個模型中定義的詞彙來建立一份功能或主要使用者劇本的清單。 將這些功能指派給反覆項目，以便能大致上平衡整個專案估計的工作負載。 這些指派之後將在此專案中變更。

- 請嘗試在早期的反覆項目中實作所有最重要使用案例的簡化版本。 在後期的反覆項目中擴充這些使用案例。 這種方式有助於降低太晚在專案中發現需求或架構之缺陷而無法進行任何處置的風險。

- 在每個反覆項目即將結束前，召集需求研討會來詳細定義將於下一個反覆項目中開發的需求或使用者劇本。 邀請可以決定優先順序的使用者和商務專案關係人，以及開發人員和系統測試人員。 提供三個小時來定義 2 週反覆項目的需求。

- 此研討會的目標是要讓每個人都同意下一個反覆項目結束時所完成的項目。 請使用模型做為其中一項工具來協助釐清需求。 研討會的輸出是反覆運算待處理專案，也就是 Team Foundation 中的開發工作清單和中的測試套件 [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 。

- 在此需求研討會中，只在您需要決定此開發工作估計的範圍內討論該設計。 否則，請將討論主題保持在使用者可能會直接體驗的系統行為。 將需求模型與架構模型分開討論。

- 非技術性專案關係人通常只要透過您一些指引，就可以順利了解 UML 圖表。

### <a name="link-model-to-work-items"></a>將模型連結至工作專案

在需求研討會之後，請詳述該需求模型的詳細資料，並且將此模型連結至開發工作。 您可以將 Team Foundation 中的工作專案連結至模型中的專案，藉以執行此動作。

雖然您可以將任何項目連結至工作項目，不過最有用的項目如下所示：

- 描述商務規則或服務需求品質的註解。 如需詳細資訊，請參閱 [模型使用者需求](../modeling/model-user-requirements.md)。

### <a name="link-model-to-tests"></a>將模型連結至測試

您可以使用需求模型來引導接受度測試的設計。 請同時與開發工作一起建立這些測試。

若要深入瞭解這項技術，請參閱 [從模型開發測試](../modeling/develop-tests-from-a-model.md)。

### <a name="estimate-remaining-work"></a>估計剩餘的工作

需求模型可以協助您估計與每個反覆項目大小相關的專案總大小。 評估該使用案例與類別的數目和複雜度可以協助您估計所需的開發工作。 當您已經完成前幾個反覆項目時，已涵蓋需求與待涵蓋需求的比較可以提供專案剩餘部分之成本和範圍的粗略測量。

在每個反覆項目即將結束前，請檢閱未來反覆項目的需求指派。 這樣做有助於將每個反覆項目結束時的軟體狀態表示成使用案例圖中的子系統。 在進行討論時，您就可以將使用案例和使用案例擴充從其中一個子系統移至另一個子系統。

## <a name="levels-of-abstraction"></a>抽象層級

模型具有與軟體相關的抽象範圍。 最具體的模型直接代表程式碼，而最抽象的模型則代表不一定會展示於該程式碼中的商務概念。

您可以透過許多種類的圖表檢視模型。 如需模型和圖表的詳細資訊，請參閱為 [您的應用程式建立模型](../modeling/create-models-for-your-app.md)。

不同種類的圖表可用於描述不同抽象層級的設計。 許多圖表類型可用於多個層級。 下表顯示每種圖表類型的使用方式。

|設計層級|圖表類型|
|-|-|
|商務程序<br /><br /> 了解使用系統的內容可協助您了解使用者的需求。|-概念類圖表會說明商務程式中所使用的商務概念。|
|使用者需求<br /><br /> 使用者對於系統需求的定義。|-商務規則和服務需求的品質可在不同的檔中說明。|
|高階設計<br /><br /> 系統的整體結構：主要元件以及它們如何結合在一起。|-相依性圖表描述系統如何結構化為相互相依的部分。 您可以針對相依性圖表驗證程式代碼，以確保其符合架構。|
|程式碼分析<br /><br /> 您可以從程式碼產生圖表。|-相依性圖表會顯示類別之間的相依性。 更新的程式碼可以根據相依性圖表進行驗證。<br />-類別圖表會顯示程式碼中的類別。|

## <a name="external-resources"></a>外部資源

|**類別**|**連結**|
|-|-|
|**影片**|![連結至影片 ](../data-tools/media/playvideo.gif) [MSDN how Do I 影片：如何建立和使用 UML 模型和圖表 (Visual Studio 2010 旗艦) ](/previous-versions/visualstudio/visual-studio-2010/dd831853(v=vs.100))<br /><br /> ![連結至影片 ](../data-tools/media/playvideo.gif) [Channel 9：使用 Visual Studio 2010 的 UML](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-1-brainstorming-a-project)<br /><br /> ![連結至影片 ](../data-tools/media/playvideo.gif) [MSDN 如何系列： UML 工具和擴充性 (Visual Studio 2010 旗艦) ](/previous-versions/visualstudio/visual-studio-2010/dd831853(v=vs.100))|
|**論壇**|- [Visual Studio Visualization & Modeling Tools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio Visualization & Modeling SDK (DSL 工具)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**部落格**|[Microsoft DevOps](https://devblogs.microsoft.com/devops/)|
|**技術文件和日誌**|[MSDN 架構中心](/previous-versions/dn630665(v=msdn.10))<br /><br /> [Visual Studio 架構工具指南](../modeling/visual-studio-architecture-tooling-guidance.md)|

## <a name="see-also"></a>請參閱

- [在 Agile 開發中使用模型](/previous-versions/ff398061(v=vs.140))
- [建立應用程式模型](../modeling/create-models-for-your-app.md)
- [模型使用者需求](../modeling/model-user-requirements.md)
- [建立應用程式架構的模型](../modeling/model-your-app-s-architecture.md)
- [透過模型開發測試](../modeling/develop-tests-from-a-model.md)
- [建構模型方案](../modeling/structure-your-modeling-solution.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]