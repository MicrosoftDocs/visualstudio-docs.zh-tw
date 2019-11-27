---
title: 擴充圖層圖表 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bfcec64f9401fdbf79e67bee5fe8430452632fbc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301024"
---
# <a name="extend-layer-diagrams"></a>Extend layer diagrams
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以撰寫程式碼來建立和更新分層圖，以及驗證 Visual Studio 中分層圖的程式碼結構。 您可以加入出現在圖表的捷徑 (操作) 功能表中的命令、自訂拖放軌跡，以及從文字範本存取圖層模型。 您可以將這些擴充功能封裝成 Visual Studio 整合擴充功能 (VSIX)，以及將這些整合擴充功能散發給其他 Visual Studio 使用者。

 如需分層圖的詳細資訊，請參閱：

- [分層圖：參考](../modeling/layer-diagrams-reference.md)

- [分層圖：方針](../modeling/layer-diagrams-guidelines.md)

- [從程式碼建立分層圖](../modeling/create-layer-diagrams-from-your-code.md)

- [使用分層圖驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)

## <a name="prereqs"></a> 需求
 您必須在想要開發圖層擴充功能的電腦上安裝下列項目：

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- [Visual Studio 2015 的模型 SDK](https://www.microsoft.com/download/details.aspx?id=48148)

  您必須在想要執行圖層擴充功能的電腦上安裝適合的 Visual Studio 版本。 如需詳細資訊，請參閱[部署圖層模型擴充](../modeling/deploy-a-layer-model-extension.md)功能。

  若要查看哪些 Visual Studio 版本支援分層圖，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="in-this-section"></a>本節內容
 [將命令和軌跡新增至分層圖](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [在分層圖中新增自訂架構驗證](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [將自訂屬性新增至分層圖](../modeling/add-custom-properties-to-layer-diagrams.md)

 [巡覽及更新程式碼中的圖層模型](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [部署圖層模型擴充功能](../modeling/deploy-a-layer-model-extension.md)

 [分層圖擴充功能疑難排解](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a>另請參閱
 [定義和安裝模型擴充功能](../modeling/define-and-install-a-modeling-extension.md)[分層圖：參考](../modeling/layer-diagrams-reference.md)[分層圖：方針](../modeling/layer-diagrams-guidelines.md)[從程式碼建立分層圖](../modeling/create-layer-diagrams-from-your-code.md)[使用分層圖](../modeling/validate-code-with-layer-diagrams.md)從[uml 模型產生](../modeling/generate-files-from-a-uml-model.md)檔案[使用 Visual Studio API 開啟 uml 模型](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)
