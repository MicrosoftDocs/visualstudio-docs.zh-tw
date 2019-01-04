---
title: 擴充相依性圖表
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a467366ca470c17c0f52bd72ae17e766bcb284d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889315"
---
# <a name="extend-dependency-diagrams"></a>擴充相依性圖表
您可以撰寫程式碼來建立和更新相依性圖表，並驗證您的程式碼，針對 Visual Studio 中的相依性圖表的結構。 您可以加入出現在圖表的捷徑 (操作) 功能表中的命令、自訂拖放軌跡，以及從文字範本存取圖層模型。 您可以將這些擴充功能封裝成 Visual Studio 整合擴充功能 (VSIX)，以及將這些整合擴充功能散發給其他 Visual Studio 使用者。

 如需有關相依性圖表的詳細資訊，請參閱：

-   [相依性圖表中：參考](../modeling/layer-diagrams-reference.md)

-   [相依性圖表中：指導方針](../modeling/layer-diagrams-guidelines.md)

-   [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)

-   [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)

##  <a name="prereqs"></a> 需求
 您必須在想要開發圖層擴充功能的電腦上安裝下列項目：

-   Visual Studio

-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

-   Modeling SDK for Visual Studio


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


 您必須在想要執行圖層擴充功能的電腦上安裝適合的 Visual Studio 版本。 如需詳細資訊，請參閱 <<c0> [ 部署圖層模型擴充功能](../modeling/deploy-a-layer-model-extension.md)。

 若要查看哪些版本的 Visual Studio 支援相依性圖表，請參閱[architecture and modeling tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="in-this-section"></a>本節內容
 [將命令和軌跡加入至相依性圖表](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [將自訂架構驗證加入至相依性圖表](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [將自訂屬性加入至相依性圖表](../modeling/add-custom-properties-to-layer-diagrams.md)

 [巡覽及更新程式碼中的圖層模型](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [部署圖層模型擴充功能](../modeling/deploy-a-layer-model-extension.md)

 [對相依性圖表延伸模組進行疑難排解](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a>另請參閱

- [相依性圖表中：參考](../modeling/layer-diagrams-reference.md)
- [相依性圖表中：指導方針](../modeling/layer-diagrams-guidelines.md)
- [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)
- [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)
