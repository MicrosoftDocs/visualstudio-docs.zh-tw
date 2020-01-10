---
title: 在其他 Visual Studio 版本中讀取模型和圖表
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ebe4cdcefb7b823090cca8976055de5a3ebb9b1a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595406"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>在其他 Visual Studio 版本中讀取模型和圖表

在不支援模型建立的 Visual Studio 版本中開啟模型時，會以唯讀模式開啟模型。 在此模式中，您可以變更圖表的版面配置，但是無法變更模型。

若要查看哪些版本的 Visual Studio 支援模型建立，請參閱[架構和模型工具的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="obtaining-access-to-a-model-and-diagrams"></a>取得模型和圖表的存取權

若要讀取相依性圖表，您必須先使用 Visual Studio 開啟模型專案，然後在其中開啟圖表。

基於這個理由，如果您想要讀取相依性圖表，您也必須能夠存取其建立所在的模型專案。 若要這麼做，您可以從原始檔控制存取專案，或取得專案檔的複本。

> [!NOTE]
> 這不適用於透過程式碼產生的 Code Map 和 .NET 類別圖。 這些圖表可以與模型專案分開檢視。

若要讀取相依性圖表，您所需的最小檔案集如下所示：

- 您想要讀取之圖表的兩個圖表檔案，例如， **MyDiagram. classdiagram 和 MyDiagram. classdiagram. layout**。

    > [!NOTE]
    > 針對相依性圖表，您也應該擁有名為_MyDiagram_的檔案 **.layerdiagram**。

- 模型專案檔案（**mymodel>. .modelproj**）

- 根模型檔案（**ModelDefinition\MyModel.uml**）

- 圖表中所參考之任何套件的封裝檔案（**ModelDefinition\MyPackage.uml**）

## <a name="changes-that-you-can-make-in-read-only-mode"></a>您可以在唯讀模式中進行的變更

如果您在不支援模型建立的 Visual Studio 版本中開啟模型和其圖表，則無法變更模型。 也就是說，您無法變更圖表或模型總管中所顯示的項目和關聯性。 不過，您可以對圖表的版面配置進行一些變更：

- 重新排列圖表上的圖形和連接器。

- 展開和摺疊圖形。

您可以儲存這些變更。 如果您想要讓其他使用者看到您的變更，您至少必須**傳送更新的**設定檔案。

## <a name="see-also"></a>請參閱

- [相依性圖表︰參考](../modeling/layer-diagrams-reference.md)
- [建立應用程式模型](../modeling/create-models-for-your-app.md)
