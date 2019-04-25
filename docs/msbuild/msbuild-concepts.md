---
title: MSBuild 概念 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, concepts
ms.assetid: 083b8ba3-e4ad-45af-bb5d-3bc81d406131
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12f0c8f2235db4c5eb332d52a454bd0093a34b68
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842785"
---
# <a name="msbuild-concepts"></a>MSBuild 概念
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 提供基本的 XML 結構描述，讓您可用來控制組建平台建置軟體的方式。 若要指定組建中的元件以及建置它們的方式，請使用下列這四個 MSBuild 組件︰屬性、項目、工作和目標。

## <a name="related-topics"></a>相關主題

| 標題 | 說明 |
| - | - |
| [MSBuild 屬性](../msbuild/msbuild-properties.md) | 介紹屬性和屬性集合。 屬性是可用來設定組建的索引鍵/值組。 |
| [MSBuild 項目](../msbuild/msbuild-items.md) | 推出項目和項目集合。 項目是建置系統的輸入內容，通常代表檔案。 |
| [MSBuild 目標](../msbuild/msbuild-targets.md) | 解釋如何以特定順序將各項工作集合在一起成為群組，並能夠在命令列上呼叫建置流程的區段。 |
| [MSBuild 工作](../msbuild/msbuild-tasks.md) | 顯示如何建立 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 可用來執行原子建置作業的可執行程式碼單元。 |
| [比較屬性和項目](../msbuild/comparing-properties-and-items.md) | 比較 MSBuild 屬性和項目。 這兩者都可用來將資訊傳遞至工作、評估條件，以及儲存可在整個專案檔中參考的值。 |
| [MSBuild 特殊字元](../msbuild/msbuild-special-characters.md) | 說明如何逸出某些 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 特別保留來在特定內容中使用的字元。 |
| [逐步解說：從頭開始建立 MSBuild 專案檔](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | 顯示如何僅使用文字編輯器來累加建立基本專案檔。 |
| [逐步解說：使用 MSBuild](../msbuild/walkthrough-using-msbuild.md) | 介紹 MSBuild 的建置區塊，以及示範如何在不關閉 Visual Studio 整合式開發環境 (IDE) 的情況下，撰寫和管理 MSBuild 專案及進行偵錯。 |
| [MSBuild 參考](../msbuild/msbuild-reference.md) | 包含參考資訊的文件連結。 |
| [MSBuild](../msbuild/msbuild.md) | 提供了專案檔的 XML 結構描述概觀，並示範如何控制建置軟體的程序。 |
