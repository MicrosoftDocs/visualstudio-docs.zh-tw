---
title: 一個方案中有多個 DSL
description: 瞭解如何將數個特定領域的語言封裝 (Dsl) 成為單一解決方案的一部分，以便將它們一起安裝。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1fbadc93f6245427284ea10c1cdd7cf99c5a7f68
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363088"
---
# <a name="multiple-dsls-in-one-solution"></a>一個方案中有多個 DSL

您可以將數個 DSL 封裝成單一方案的一部分，以便能夠一起安裝。

用來整合多個 DSL 的方法有幾種。 如需詳細資訊，請參閱 [使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md) 和 how [To：新增拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md) 和 [自訂複製行為](../modeling/customizing-copy-behavior.md)。

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>在相同的解決方案中建立一個以上的 DSL

1. 建立新的 **VSIX 專案** 專案。

2. 在 VSIX 解決方案目錄中建立兩個或多個 DSL 專案。

   - 針對每個 DSL，開啟 Visual Studio 的新執行個體。 建立新的 DSL，然後指定與 VSIX 方案相同的方案資料夾。

   - 確定使用不同的副檔名建立各個 DSL。

   - 變更 **Dsl** 和 **DslPackage** 專案的名稱，使其全部不同。 例如：`Dsl1`、`DslPackage1`、`Dsl2`、`DslPackage2`。

   - 在每個 **DslPackage \* \ source.extension.tt** 中，將這一行更新為正確的 Dsl 專案名稱：

      `string dslProjectName = "Dsl2";`

   - 在 VSIX 方案中，加入 Dsl * 和 DslPackage \* 專案。 您可能想將每組專案置於各自的方案資料夾中。

2. 合併 DSL 的 VSIX 資訊清單：

   1. 開啟 _您 vsix 專案_**\source.extension.manifest**。

   2. 針對每個 DSL，選擇 [ **新增內容** ]，然後新增：

       - `Dsl*`作為 **MEF 元件** 的專案

       - `DslPackage*`作為 **MEF 元件** 的專案

       - `DslPackage*` 專案為 **VS 封裝**

3. 建置方案。

   產生的 VSIX 會同時安裝這兩個 DSL。 您可以使用 F5 來測試它們，或部署 _您 vsix 專案_**\bin\Debug \\ \* .vsix**。

## <a name="see-also"></a>請參閱

- [使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [如何：加入拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [自訂複製行為](../modeling/customizing-copy-behavior.md)