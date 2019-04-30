---
title: 一個方案中有多個 DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87d9e4ae8239994a7524cdd1da0b3cfe05ea42d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808180"
---
# <a name="multiple-dsls-in-one-solution"></a>一個方案中有多個 DSL

您可以將數個 DSL 封裝成單一方案的一部分，以便能夠一起安裝。

用來整合多個 DSL 的方法有幾種。 如需詳細資訊，請參閱 <<c0> [ 使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)和[How to:新增拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)並[自訂複製行為](../modeling/customizing-copy-behavior.md)。

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>建置在相同方案中的多個 DSL

1. 建立新**VSIX 專案**專案。

2. 建立兩個或多個 DSL 專案的 VSIX 方案目錄中。

   - 針對每個 DSL，開啟 Visual Studio 的新執行個體。 建立新的 DSL，然後指定與 VSIX 方案相同的方案資料夾。

   - 確定使用不同的副檔名建立各個 DSL。

   - 變更的名稱**Dsl**並**DslPackage**專案，使其完全不同。 例如：`Dsl1`、`DslPackage1`、`Dsl2`、`DslPackage2`。

   - 在每個**DslPackage\*\source.extension.tt**，這行更新為正確的 Dsl 專案名稱：

      `string dslProjectName = "Dsl2";`

   - 在 VSIX 方案中，加入 Dsl * 和 DslPackage\*專案。 您可能想將每組專案置於各自的方案資料夾中。

2. 合併 DSL 的 VSIX 資訊清單：

   1. 開啟_您的 vsix 專案_**\source.extension.manifest**。

   2. 針對每個 DSL 中，選擇**加入內容**並新增：

       - `Dsl*` 專案做為**MEF 元件**

       - `DslPackage*` 專案做為**MEF 元件**

       - `DslPackage*` 專案做為**VS 套件**

3. 建置方案。

   產生的 VSIX 會同時安裝這兩個 DSL。 您可以使用 f5 鍵，就可以將它測試它們，或部署_您的 vsix 專案_**\bin\Debug\\\*.vsix**。

## <a name="see-also"></a>另請參閱

- [使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [如何：新增拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [自訂複製行為](../modeling/customizing-copy-behavior.md)