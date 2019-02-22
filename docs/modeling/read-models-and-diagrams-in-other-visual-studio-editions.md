---
title: 在其他 Visual Studio 版本中讀取模型和圖表
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5363a4d2f07b22aa0a256ff40f039792a3d2a6c2
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55932192"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>在其他 Visual Studio 版本中讀取模型和圖表

在不支援模型建立的 Visual Studio 版本中開啟模型時，會以唯讀模式開啟模型。 在此模式中，您可以變更圖表的版面配置，但是無法變更模型。

若要查看哪些版本的 Visual Studio 支援模型建立，請參閱[architecture and modeling tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="obtaining-access-to-a-model-and-diagrams"></a>取得模型和圖表的存取權

若要讀取的相依性圖表，您必須先使用 Visual Studio 開啟模型專案中，，然後開啟 其內圖表。

基於這個理由，如果您想要讀取相依性圖表中，您也必須在其中建立模型專案的存取權。 您可以藉由存取 從原始檔控制專案或取得專案檔的複本。

> [!NOTE]
> 這不適用於透過程式碼產生的 Code Map 和 .NET 類別圖。 這些圖表可以與模型專案分開檢視。

若要讀取的相依性圖表，您需要的檔案的最小集如下所示：

-   兩個圖表檔，例如，想要讀取之圖表**MyDiagram.classdiagram 和 MyDiagram.classdiagram.layout**。

    > [!NOTE]
    > 如需相依性圖表中，您還要有檔案，稱為_MyDiagram_**。 layerdiagram.suppressions**。

-   模型專案檔 (**MyModel.modelproj**)

-   根模型檔 (**ModelDefinition\MyModel.uml**)

-   在圖表中所參考之任何套件的套件檔案 (**ModelDefinition\MyPackage.uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>您可以在唯讀模式中進行的變更

如果您在不支援模型建立的 Visual Studio 版本中開啟模型和其圖表，則無法變更模型。 也就是說，您無法變更圖表或模型總管中所顯示的項目和關聯性。 不過，您可以對圖表的版面配置進行一些變更：

- 重新排列圖表上的圖形和連接器。

- 展開和摺疊圖形。

您可以儲存這些變更。 如果您想要讓您變更其他使用者看到，您必須至少傳送更新過 **.layout**檔案。

## <a name="see-also"></a>另請參閱

- [相依性圖表中：參考](../modeling/layer-diagrams-reference.md)
- [建立應用程式模型](../modeling/create-models-for-your-app.md)