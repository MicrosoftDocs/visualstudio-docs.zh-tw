---
title: 擴充相依性圖表
description: 瞭解如何撰寫程式碼以建立和更新相依性圖表，以及如何根據 Visual Studio 中的相依性圖表驗證程式代碼的結構。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d78b7005875f0544354c845cd27d187bdbf40d6d
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361621"
---
# <a name="extend-dependency-diagrams"></a>擴充相依性圖表

您可以撰寫程式碼來建立和更新相依性圖表，以及根據 Visual Studio 中的相依性圖表驗證程式代碼的結構。 您可以加入出現在圖表的捷徑 (操作) 功能表中的命令、自訂拖放軌跡，以及從文字範本存取圖層模型。 您可以將這些擴充功能封裝成 Visual Studio 整合擴充功能 (VSIX)，以及將這些整合擴充功能散發給其他 Visual Studio 使用者。

## <a name="requirements"></a>規格需求

您必須在想要開發圖層擴充功能的電腦上安裝下列項目：

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- Visual Studio 的模型化 SDK

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

您必須在要執行圖層擴充功能的電腦上安裝適當的 Visual Studio 版本。 若要查看 Visual Studio 支援相依性圖表的版本，請參閱 [架構和模型工具的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="see-also"></a>請參閱

- [相依性圖表︰參考](../modeling/layer-diagrams-reference.md)
- [相依性圖表︰方針](../modeling/layer-diagrams-guidelines.md)
- [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)
- [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)
