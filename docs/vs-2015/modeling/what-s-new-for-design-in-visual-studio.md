---
title: 什麼&#39;的新設計
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- what's new [VIsual Studio], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 148da7602d8198a4c85e2a7fbee2107b4e9662d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187128"
---
# <a name="whats-new-for-design-in-visual-studio-in-visual-studio-2015"></a>在 Visual Studio 2015 的 Visual Studio 中設計的最新消息
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
這個版本的 Visual Studio 包括下列改進，協助您進一步了解和設計程式碼。

 **Code Map 和相依性圖形**

 在 Visual Studio Enterprise 中，當您想要了解程式碼中的特定相依性時，請建立 Code Map 來將其視覺化。 然後，您可以使用出現在您程式碼旁邊的對應，來巡覽這些關聯性。 Code Map 也可以在您工作或偵錯程式碼時，協助追蹤您在程式碼中的位置，如此一來，當您進一步了解程式碼設計時，便可以少看一些程式碼。

 在最終 (RTM) 發行版本中，我們將命令分組成與選取、編輯和管理群組相關的區段，並變更群組內容的配置，以更容易使用程式碼項目和連結的捷徑功能表。 另請注意，測試專案的顯示樣式會與其他專案不同，並且我們已將對應上的項目圖示更新為更適當的版本。

 ![新的 code map 上顯示選取的項目](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 其他改進還包括：

- **改進由上而下的圖表**。 針對中大型 Visual Studio 方案，您現在可以使用簡化的 [架構] 功能表，取得對方案更實用的 Code Map。 方案的組件會依方案資料夾分組，因此您可以在內容中查看，並且利用之前建構方案的辛勞成果。 您會立即看到專案和組件參考，並接著顯示連結類型。 此外，方案的外部組件也會以更精簡的方式分組。

- **測試專案已有不同的樣式並可篩選**。 由於對應上的測試專案具有不同的樣式，因此您現在可以更輕鬆快速地識別這些專案。 您也可以篩選專案，以專注於應用程式的使用中程式碼。

- **簡化外部相依性連結**。 相依性連結不再繼承自 System.Object、System.ValueType、System.Enum 和 System.Delegate，因此您可以在 Code Map 中更輕鬆地查看外部相依性。

- **「向內切入相依性連結」會將篩選納入考量**。 當您展開以了解相依性連結的比重時，可以獲得一目暸然的實用圖表。 這個圖表較整齊，也會將您所選取的連結篩選選項列入考量。

- **程式碼項目會連同其內容加入 Code Map**。 由於圖表現在會連同其內容一起顯示 (最上層為可視需要篩選出的組件和方案資料夾)，因此當您從方案總管、類別檢視、物件瀏覽器拖放程式碼項目時，或者在方案總管中選取項目並選擇 [在 Code Map 上顯示] 時，您會獲得更實用的圖表。

- **更快取得反應靈敏的 Code Map**。 拖放作業會產生立即結果，並且可更快速地建立節點之間的連結，而不會影響後續使用者啟動的作業 (例如展開節點或要求更多節點)。 當您在不建置方案的情況下建立 Code Map 時，現在會處理所有極端案例 (例如未建置組件時)。

- **略過重建方案。** 在建立及編輯圖表時提升效能。

- **篩選程式碼項目節點和群組**。 您可以根據程式碼項目的類別來顯示或隱藏程式碼項目，也可以依照方案資料夾、組件、命名空間、專案資料夾和類型分組程式碼項目，以快速地整理對應。

- **篩選關聯性以更容易閱讀圖表**。 連結篩選現在也適用於跨群組連結，因此使用篩選視窗的干擾比舊版更低。

- **從類別檢視和物件瀏覽器建立圖表**。 將檔案和組件從類別檢視和物件瀏覽器拖放到新的或現有的對應中。

  請參閱 [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md)。

  **本版中的其他設計和模型變更：**

- **分層圖**。 使用類別檢視和物件瀏覽器來更新這些圖表。 為了達到軟體設計需求，請使用分層圖來描述軟體所需的相依性。 透過尋找不符合這些條件約束的程式碼，並使用這個基準來驗證未來的程式碼，讓程式碼與這個設計保持一致。

- **UML 圖表**。 您已無法再從程式碼建立 UML 類別圖和循序圖。 但您還是可以使用新的 UML 元素來建立這些圖表。

- **架構總管**。 您已無法再使用架構總管來建立圖表。 但您還是可以使用方案總管。

## <a name="VersionSupport"></a> Architecture and modeling tools 的版本支援

Visual Studio 2015 有數個版本。 並非所有版本都提供 architecture and modeling tools 的支援。 下表顯示每個工具的可用性。

|**功能**|**企業**|**Professional**|**Community**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Code Map**|是|只支援讀取和篩選 code map、 加入新的泛型節點，以及從選取範圍建立新的導向圖形。|-|-|
|**UML 類別圖表**|是|-|-|-|
|**UML 順序圖表**|是|-|-|-|
|**UML 使用案例圖表**|是|-|-|-|
|**UML 活動圖表**|是|-|-|-|
|**UML 元件圖**|是|-|-|-|
|**分層圖**|是|-|-|-|
|**有向圖形**（DGML 圖表）|是|是|-|-|
|**程式碼複製品**|是|-|-|-|