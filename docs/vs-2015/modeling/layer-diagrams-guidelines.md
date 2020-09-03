---
title: 分層圖：方針 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 2903bec7-a93b-46a6-aac6-994ac4f3f1a7
caps.latest.revision: 57
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21376668eef88d3d8ce42ff73785b972be045cb2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850639"
---
# <a name="layer-diagrams-guidelines"></a>圖層圖表：方針
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中建立 *分層圖* ，以高層級描述您的應用程式架構。 使用分層圖驗證程式碼，以確定程式碼與設計保持一致。 您也可以在建置流程中包含圖層驗證。 請參閱 [Channel 9 影片：使用分層圖設計和驗證架構](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)。

 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="what-is-a-layer-diagram"></a>圖層圖表是什麼?
 圖層圖表就像傳統架構圖表一樣會識別主要元件或功能性的設計單位及其相依性。 圖表上的每個節點稱為「 *圖層*」，表示命名空間、專案或其他成品的邏輯群組。 您可以繪製應該存在於您設計中的相依性。 與傳統架構圖表不同的是，您可以在原始程式碼中驗證實際的相依性是否符合所指定的預期相依性。 在 [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] 上製作正常組建的驗證部分，就可以確保程式碼即使日後變更仍然會繼續依照系統架構。 請參閱 [分層圖：參考](../modeling/layer-diagrams-reference.md)。

## <a name="how-to-design-or-update-your-app-with-layer-diagrams"></a><a name="Update"></a> 如何使用分層圖設計或更新您的應用程式
 下列步驟概述了如何在開發程序內使用圖層圖表。 本主題稍後的章節會描述每個步驟的更多相關詳細資料。 如果您正在開發新的設計，請略過參考現有程式碼的步驟。

> [!NOTE]
> 這些步驟會按大致順序出現。 您可能會想要重疊工作、重新排序以符合自己的情況，以及從專案中每個反覆項目的開頭重新瀏覽。

1. 為整個應用程式或圖層內的圖層[建立圖層圖表](#Create)。

2. [定義圖層以代表應用程式的主要功能區域或元件](#CreateLayers) 。 根據這些圖層的功能，例如「簡報」或「服務」來為圖層命名。 如果您有 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 解決方案，則可以將每個圖層與成品集合 *（* 例如專案、命名空間、檔案等）產生關聯。

3. 探索各層之間[的現有](#Generate)相依性。

4. [編輯圖層和](#EditArchitecture) 相依性，以顯示您想要程式碼反映的更新設計。

5. 藉由建立圖層來代表主體架構區塊或元件，並定義相依性以顯示每一層如何使用其他層級，來[設計應用程式的新區域](#NewAreas)。

6. [編輯圖表的版面配置和外觀](#EditLayout) ，以協助您與同事討論。

7. [針對分層圖驗證程式代碼](#Validate) ，以醒目提示程式碼與所需架構之間的衝突。

8. [更新程式碼以符合新的架構](#UpdateCode)。 反覆開發和重構程式碼直到驗證顯示沒有衝突。

9. [在組建流程中包含圖層驗證](#BuildValidation) ，以確保程式碼繼續遵守您的設計。

## <a name="create-a-layer-diagram"></a><a name="Create"></a> 建立分層圖
 您必須在模型專案之內建立圖層圖表。 您可以將新的圖層圖表加入至現有的模型專案、為圖層圖表建立新的模型專案，或在相同的模型專案中複製現有的圖層圖表。

> [!IMPORTANT]
> 不要從模型專案將現有圖層圖表加入、拖曳、複製到其他模型專案或方案中的其他位置。 以這種方式複製的圖層圖表即使在修改之後也會有與原始圖表相同的參考。 這樣會導致圖層驗證無法正確執行，同時可能會造成其他問題，例如項目遺失或嘗試開啟圖表時發生其他錯誤。

 請參閱 [從您的程式碼建立圖層圖表](../modeling/create-layer-diagrams-from-your-code.md)。

## <a name="define-layers-to-represent-functional-areas-or-components"></a><a name="CreateLayers"></a> 定義圖層以代表功能區域或元件
 圖層代表 *構件*的邏輯群組，例如專案、程式碼檔案、命名空間、類別和方法。 您可以從 Visual C# .NET 和 Visual Basic.NET 專案的成品中建立圖層，或可以透過連結文件 (例如 Word 檔案或 PowerPoint 簡報) 將規格或計劃附加至圖層。 每個圖層都會顯示為圖表上的矩形，並顯示連結到圖層的成品數目。 圖層可以包含巢狀圖層以描述更特定的工作。

 一般來說，會根據圖層的函式 (例如，「簡報」或「服務」) 來為圖層命名。 如果成品具有密切相依性，請將它們放在同一圖層。 如果成品可以個別更新或用於個別應用程式，請將它們放在不同的圖層中。 若要深入瞭解如何分層模式，請造訪 & 實務的模式網站 [http://go.microsoft.com/fwlink/?LinkId=145794](https://apparch.codeplex.com/Wiki/View.aspx?title=Application Patterns&referringTitle=Home) 。

> [!TIP]
> 某些類型的成品可以連結至圖層，但是不支援針對圖層圖表進行驗證。 若要查看成品是否支援驗證，請開啟 [ **圖層瀏覽器** ] 以檢查成品連結的 [ **支援驗證** ] 屬性。 請參閱 [探索各圖層之間的現有](#Generate)相依性。

 更新不熟悉的應用程式時，您可能也會建立 Code Map。 這些圖表可協助您在瀏覽程式碼時探索模式和相依性。 使用 [方案總管] 探索命名空間和類別，這通常會正確對應至現有的圖層。 將程式碼成品從 [方案總管] 拖曳至分層圖，可將其指派至圖層。 接著可以使用分層圖協助您更新程式碼，並讓它與設計保持一致。

 請參閱：

- [從程式碼建立分層圖](../modeling/create-layer-diagrams-from-your-code.md)

- [使用 Code Map 偵錯您的應用程式](../modeling/use-code-maps-to-debug-your-applications.md)

- [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)

## <a name="discover-existing-dependencies-between-layers"></a><a name="Generate"></a> 探索圖層之間的現有相依性
 只要與某個圖層關聯的成品參考到與另一個圖層關聯的成品，相依性便會存在。 例如，某個圖層中的類別會宣告在另一個圖層中具有類別的變數。 您可以讓相依性進行反向工程以找出現有的相依性。

> [!NOTE]
> 您無法針對特定種類的成品進行其相依性的反向工程。 例如，對連結到文字檔的圖層進行反向工程時，無法找出與該圖層之間的任何相依性。 若要查看哪些成品具有您可以進行反向工程的相依性，請在一或多個圖層上按一下滑鼠右鍵，然後按一下 [ **View Links**]。 在 [ **圖層瀏覽器**] 中，檢查 [ **支援驗證** ] 資料行。 相依性不會針對此資料行顯示為 **False**的成品進行反向工程。

#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>在圖層之間對現有相依性進行反向工程

- 選取一或多個圖層，以滑鼠右鍵按一下選取的圖層，然後按一下 [產生相依性 **]**。

  通常，您會看到一些不應該存在的相依性。 您可以編輯這些相依性，以便與預期的設計保持一致。

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditArchitecture"></a> 編輯圖層和相依性以顯示預期的設計
 若要描述您打算對系統或預期架構進行的變更，請使用下列步驟來編輯圖層圖表。 您也可以考慮先進行一些重構變更來改善程式碼結構，然後再擴充。 請參閱 [改善程式碼的結構](#Improving)。

|**若要**|**執行這些步驟**|
|------------|-----------------------------|
|刪除不應該存在的相依性|按一下 [相依性]，然後按 [ **刪除**]。|
|變更或限制相依性的方向|設定其 **Direction** 屬性。|
|建立新的相依性|使用相依 **性** 和 **雙向** 相依性工具。<br /><br /> 若要繪製多個相依性，請按兩下工具。 當您完成時，請按一下 [ **指標** ] 工具，或按 **ESC** 鍵。|
|指定與圖層關聯的成品不可相依於指定的命名空間|在圖層的 [禁止的 **命名空間** 相依性] 屬性中輸入命名空間。 使用分號 (**;**) 來分隔命名空間。|
|指定與圖層關聯的成品不可屬於指定的命名空間|在圖層的 [禁止的 **命名空間** ] 屬性中輸入命名空間。 使用分號 (**;**) 來分隔命名空間。|
|指定與圖層關聯的成品必須屬於其中一個指定的命名空間|在圖層的 [必要的 **命名空間** ] 屬性中輸入命名空間。 使用分號 (**;**) 來分隔命名空間。|

### <a name="improving-the-structure-of-the-code"></a><a name="Improving"></a> 改善程式碼的結構
 重構變更屬於改良功能，不會影響應用程式的行為，但是可協助讓程式碼變得更容易變更和在日後進行擴充。 結構完善的程式碼具有易於抽象至圖層圖表的設計。

 例如，如果您為程式碼中每個命名空間建立圖層，然後對相依性進行反向工程，則圖層之間應該會有最小一組的單向相依性。 如果您使用類別或方法做為圖層來建立更詳細的圖表，則結果應該也會有相同的特性。

 如果不是這樣，那麼程式碼就會較難在其生命週期中有所變更，並且會較不適合使用圖層圖表進行驗證。

## <a name="design-new-areas-of-your-application"></a><a name="NewAreas"></a> 設計應用程式的新區域
 當您著手開發新專案或新專案的新區域時，可以繪製圖層與相依性，以便有助您先識別主要元件，再著手開發程式碼。

- 盡可能在圖層圖表中**顯示可辨識的架構模式**。 例如，描述桌面應用程式的圖層圖表可能包括簡報、網域邏輯和資料儲存區等圖層。 涵蓋應用程式內單一功能的圖層圖表可能具有例如模型、檢視和控制器等的圖層。 如需這類模式的詳細資訊，請參閱 [模式 & 實務：應用程式架構](https://apparch.codeplex.com/Wiki/View.aspx?title=Application Patterns&referringTitle=Home)。

     如果您經常建立類似的模式，請建立自訂工具。 請參閱 [定義自訂模型工具箱專案](../modeling/define-a-custom-modeling-toolbox-item.md)。

- **為每個圖層** （例如命名空間、類別或元件）建立程式碼成品。 這可讓您更容易地遵循程式碼，並將程式碼成品連結至圖層。 一旦建立每個成品後，請將它連結至適當的圖層。

- **您不需要將大部分的類別和其他成品連結到圖層** ，因為它們落在較大型的成品中，例如您已經連結到圖層的命名空間。

- **建立新功能的新圖表**。 一般而言，會有一個或多個描述整個應用程式的圖層圖表。 如果您要在應用程式內設計新功能，請勿加入或變更現有的圖表。 相反地，請建立自己圖表，以反映程式碼的新組件。 新圖表中的圖層可能包括簡報、網域邏輯和新功能的資料庫層。

     在建置應用程式時，會針對整體圖表和更詳細的功能圖表來驗證您的程式碼。

## <a name="edit-the-layout-for-presentation-and-discussion"></a><a name="EditLayout"></a> 編輯簡報和討論的版面配置
 若要協助您識別圖層與相依性，或與小組成員進行討論，請以下列方式編輯圖表的外觀和版面配置：

- 變更圖層的大小、圖形和位置。

- 變更圖層和相依性的色彩。

  - 選取一或多個圖層或相依性，按一下滑鼠右鍵，然後按一下 [ **屬性**]。 在 [ **屬性** ] 視窗中，編輯 [ **色彩** ] 屬性。

## <a name="validate-the-code-against-the-diagram"></a><a name="Validate"></a> 針對圖表驗證程式代碼
 若已編輯圖表，您可以隨時手動針對程式碼驗證圖表，或在每次執行本機組建或 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] 時自動驗證。

 請參閱：

- [使用分層圖驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)

- [在建置流程中包含圖層驗證](#BuildValidation)

## <a name="update-the-code-to-conform-to-the-new-architecture"></a><a name="UpdateCode"></a> 更新程式碼以符合新的架構
 通常，會在您第一次針對更新的圖層圖表驗證程式碼時出現錯誤。 這些錯誤可以有數個原因：

- 成品指派給錯誤的圖層。 在此情況下，請移動成品。

- 類別之類的成品以與架構發生衝突的方式使用另一個類別。 在此情況下，請重構程式碼以移除相依性。

  若要解決這些錯誤，請更新程式碼直到驗證時不再出現錯誤為止。 這通常是反覆的程序。 如需這些錯誤的詳細資訊，請參閱 [使用分層圖驗證程式代碼](../modeling/validate-code-with-layer-diagrams.md)。

> [!NOTE]
> 隨著您開發或重構程式碼，您可能會有新成品要連結至圖層圖表。 不過，這可能不是必要的，比方說在您有代表現有命名空間的圖層，而新的程式碼只會將更詳細的資料加入至這些命名空間時。

 在開發過程中，您可以隱藏驗證期間已報告過的某些衝突。 例如，您可能會想要隱藏已經處理的錯誤，或是與特定情節無關的錯誤。 當您隱藏錯誤時，最好在 [!INCLUDE[esprfound](../includes/esprfound-md.md)] 中記錄工作項目。 若要執行這項工作，請參閱 [使用分層圖驗證程式代碼](../modeling/validate-code-with-layer-diagrams.md)。

## <a name="include-layer-validation-in-the-build-process"></a><a name="BuildValidation"></a> 在組建流程中包含圖層驗證
 若要確保程式碼的日後變更符合圖層圖表，請在您的方案標準建置流程中包含圖層驗證。 不論其他小組成員何時建置方案，只要程式碼與圖表圖層中的相依性之間有任何差異，將會報告為建置錯誤。 如需在組建流程中包含圖層驗證的詳細資訊，請參閱 [使用分層圖驗證程式代碼](../modeling/validate-code-with-layer-diagrams.md)。

## <a name="see-also"></a>另請參閱
 [分層圖：參考](../modeling/layer-diagrams-reference.md)[從程式碼建立分層圖](../modeling/create-layer-diagrams-from-your-code.md)
