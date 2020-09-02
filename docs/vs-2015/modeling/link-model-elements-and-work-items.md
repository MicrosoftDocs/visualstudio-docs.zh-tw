---
title: 連結模型專案和工作專案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.common.removeworkitemsdialog
- vs.teamarch.common.linkworkitemsdialog
helpviewer_keywords:
- UML - extending, linking to TFS work items
- UML - extending, linking work items
- work items, creating from UML models
- UML model, creating work items
- work items, linking to UML models
- UML model, linking work items
ms.assetid: e687a490-0f93-412c-a1ff-eea83cf7ba07
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ee4fea9e3fb1d5b4d27b1d520ac2ab036747f73d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657635"
---
# <a name="link-model-elements-and-work-items"></a>連結模型項目和工作項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

透過連結 Visual Studio 中的模型項目與 Team Foundation Server 或 Visual Studio Team Services 中的工作項目來追蹤工作、測試案例、Bug、需求，問題及其他與您的模型相關的工作。 附加文件至連結的工作項目，使工作項目與模型項目相關聯。

 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

> [!NOTE]
> 您必須使用 Team Explorer 建立與開啟連結。 請確定您的模型專案和圖表已簽入版本控制，以便其他人可開啟所連結的圖表。

 例如，您可以連結：

- 顯示劇本如何實現為一連串作業的「使用者劇本」工作項目與活動圖。

- 使用案例圖中的使用案例與測試工作項目，以確保正確實作使用案例。

- 將 UML 類別圖上類別中的屬性，以及與屬性實作中錯誤相關的 Bug 工作項目。

- 元件圖中的元件以及追蹤元件開發的「工作」(Task) 工作項目。 這類工作通常會細分為較小的工作

  您可以將工作項目連結至任何可在模型圖表或在 [UML 模型總管] 中選取的項目，例如：

- UML 模型中的所有項目，例如 UML 類別、生命線、使用案例、子系統、活動、物件節點、元件和介面。

- UML 模型中的所有關聯 (Relation)，例如關聯 (Association)、一般化、相依性、流程和訊息。

- 項目的組成部分，例如類別的屬性和作業、生命線的執行次數、活動的輸入和輸出連接，以及元件的組件和連接埠。

- 圖層和圖層相依性。

- 註解和註解連結。

- 圖表。 若要選取圖表，請選擇圖表的空白部分。

> [!WARNING]
> 您必須先連接 TFS 原始程式碼控制 (SCC) 才能建立或連結工作項目。 若您嘗試開啟連接至不同的 TFS SCC，Visual Studio 會自動關閉目前方案。 請先確認您已連接至適當的 SCC，再嘗試建立或連結至工作項目。 在更新版本的 Visual Studio 中，如果沒有連接至 SCC 即無法使用功能表命令。

- [連接到 Team 專案](#ConnectTFS)

- [將模型項目連結至新的工作項目](#LinkNew)

- [將模型項目連結至現有的工作項目](#LinkExisting)

- [檢視連結至模型項目的工作項目](#OpenWorkItem)

- [檢視連結至工作項目的模型項目](#ViewLinkedModels)

- [刪除模型項目和工作項目之間的連結](#RemoveLinks)

- [疑難排解](#Troubleshooting)

## <a name="connect-to-a-team-project"></a><a name="ConnectTFS"></a> 連接至 team 專案
 您必須先連接到 Team 專案以建立、檢視或移除連結。

1. 在 [小組] **** 功能表上，選擇 [管理連線] **** 以顯示 Team Explorer 視窗。

2. 如果未出現正確的專案，在 Team Explorer 中依序選擇 [管理連線] **** 、 [連接到 Team 專案] ****。 此時請選擇正確的專案，若有需要也可選擇伺服器。

3. 在 [ **Team Explorer**] 中，選擇您想要建立、連結或檢視工作項目的專案。

## <a name="link-a-model-element-to-a-new-work-item"></a><a name="LinkNew"></a> 將模型專案連結至新的工作專案

1. 請務必連接到您要使用的 TFS 執行個體。

2. 在模型圖表或在 [ **UML 模型總管**] 上，開啟模型項目的捷徑功能表。

3. 選擇 [ **建立工作項目** ] 和您所要建立的工作項目類型。

4. 填寫在工作項目表單中的欄位。 選擇 [ **儲存工作項目**]。

     Visual Studio 會將模型項目連結至新的工作項目。 模型項目之上或旁邊會出現一個圖示。

> [!WARNING]
> 您必須先連接 TFS 原始程式碼控制 (SCC) 才能建立或連結工作項目。 若您嘗試開啟連接至不同的 TFS SCC，Visual Studio 會自動關閉目前方案。 請先確認您已連接至適當的 SCC，再嘗試建立或連結至工作項目。 在更新版本的 Visual Studio 中，如果沒有連接至 SCC 即無法使用功能表命令。

## <a name="link-a-model-element-to-an-existing-work-item"></a><a name="LinkExisting"></a> 將模型專案連結至現有的工作專案
 當您將模型項目連結至工作項目時，請從模型項目開始，而非工作項目。

1. 請務必連接到您要使用的 TFS 執行個體。

2. 在模型圖表或在 [ **UML 模型總管**] 上，開啟模型項目的捷徑功能表。 選擇 [ **連結至工作項目**]。 在 [ **專案** ] 欄位中選取您的專案。

3. 遵循下列其中一個步驟來選擇一個或多個要連結至模型項目的工作項目：

    - 在 [ **已儲存的查詢**] 中選擇查詢。

    - 在 **ID**中輸入一個或多個工作項目的 ID，並以空格隔開。

    - 在 [ **標題包含**] 中輸入單字或片語。

4. 選擇 [ **尋找**]。

5. 在工作項目清單中，選取您要連結的工作項目。

     當您完成時，模型項目的 [ **工作項目** ] 屬性就會顯示比先前更大的數目。 模型項目之上或旁邊也會出現一個圖示。

> [!WARNING]
> 您必須先連接 TFS 原始程式碼控制 (SCC) 才能建立或連結工作項目。 若您嘗試開啟連接至不同的 TFS SCC，Visual Studio 會自動關閉目前方案。 請先確認您已連接至適當的 SCC，再嘗試建立或連結至工作項目。 在更新版本的 Visual Studio 中，如果沒有連接至 SCC 即無法使用功能表命令。

## <a name="view-work-items-linked-to-a-model-element"></a><a name="OpenWorkItem"></a> 查看連結至模型專案的工作專案

1. 在 **Team Explorer**中，確定您已經連接到工作項目連結至模型項目所在的 Team 專案。

2. 在模型圖表或在 [ **UML 模型總管**] 上，開啟模型項目的捷徑功能表。 選擇 [ **檢視工作項目** ] 以檢視連結的工作項目清單。

    > [!NOTE]
    > 僅會顯示目前連接之伺服器的工作項目。 如果您沒有看到任何工作項目，請確定您已連接至 [ **Team Explorer**] 中的正確伺服器。

## <a name="view-model-elements-linked-to-a-work-item"></a><a name="ViewLinkedModels"></a> 視圖連結至工作專案的模型元素
 您可以檢視連結至 Visual Studio Team Services 及 Team Foundation Server 2012 (含) 以後版本中工作項目的模型圖表與項目。 例如，工作項目可能連接到類別模型，以顯示要實作的新類別設計。

1. 在 **Team Explorer**中，確定您已經連接到模型項目連結至工作項目所在的 Team 專案。

    > [!NOTE]
    > 您只能使用 Team Explorer 檢視連結的模型項目，不能使用 Team Web Access 檢視。 確定您的工作區已對應至包含模型圖表或項目的模型專案。 如果您沒有工作區，則必須建立一個。 請參閱 [疑難排解](#Troubleshooting) 和 [建立和使用工作區](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a)。

2. 開啟工作項目，選擇 [ **連結**]。 在 [ **模型連結**] 底下，開啟所連結模型項目的捷徑功能表。 選擇 [ **開啟連結項目**]。

     ![從工作項目開啟連結的模型項目](../modeling/media/workitem-openlinkedmodelelement.png "WorkItem_OpenLinkedModelElement")

## <a name="delete-links-between-model-elements-and-work-items"></a><a name="RemoveLinks"></a> 刪除模型專案和工作專案之間的連結
 從模型項目開始移除連結的工作項目。 這樣就可將模型項目的交互連結從工作項目移除。 反之，如果您從工作項目開始，則從模型項目到工作項目的交互連結將不會被刪除。

1. 在模型圖表或在 [ **UML 模型總管**] 上，開啟模型項目的捷徑功能表。

2. 選擇 [ **移除工作項目**]。

     \- 或 -

    1. 選擇 [ **屬性**]，再選擇顯示連結工作項目數量的 [ **工作項目** ]。

    2. 在 [ **工作項目** ] 屬性中，選擇省略符號按鈕 **[…]**。

        > [!NOTE]
        > 只會顯示目前伺服器上的工作項目。 如果清單是空的，但工作項目數目不是零，請確認您是否連接到 [ **Team Explorer**] 中正確的伺服器。

3. 在 [ **移除工作項目的連結**] 下，清除您要取消連結的所選項目。 選擇 [確定]。

## <a name="troubleshooting"></a><a name="Troubleshooting"></a> 疑難排解

|**問題**|**可能的原因**|**解決方法**|
|---------------|------------------------|--------------------|
|找不到您要連結的模型項目。|此項目可能在 [!INCLUDE[esprscc](../includes/esprscc-md.md)]中模型專案的圖表上。 您可能沒有對應至此圖表的工作區。|請將您的工作區對應至模型專案和圖表。 如果您沒有工作區，您必須建立一個。<br /><br /> 針對這個問題所出現的錯誤訊息包含了您可以用來對應工作區的路徑。<br /><br /> 請參閱 [建立和使用工作區](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a)。|
|找不到所連結的模型項目。|連結項目可能在已經移動、重新命名或刪除的圖表上。|1. 在工作專案中，刪除模型元素的連結。<br />2. 從工作專案建立新的連結至模型專案。|
|工作項目的連結沒有您預期的連結模型項目。|只有當連結從工作項目中建立時，工作項目才會顯示連結的圖層項目。 如果您的團隊未使用 [!INCLUDE[esprscc](../includes/esprscc-md.md)]，圖表的本機路徑將會用來建立連結。 如果模型專案和它的圖表在 [!INCLUDE[esprscc](../includes/esprscc-md.md)]中，則可以存取專案的所有團隊成員都可以檢視工作項目中的連結項目。|嘗試重新整理工作項目。|
|從工作項目刪除模型項目的連結時，並不會刪除從模型項目連結至工作項目的連結。||從模型項目開始刪除工作項目的連結。|

## <a name="see-also"></a>另請參閱
 [編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)[為您的應用程式建立模型](../modeling/create-models-for-your-app.md)
