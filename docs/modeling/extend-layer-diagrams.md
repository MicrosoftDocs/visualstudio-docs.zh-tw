---
title: 擴充相依性圖表
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
ms.openlocfilehash: 305c562c7600dc6955ce0307db92f4e257fc1c21
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302942"
---
# <a name="extend-dependency-diagrams"></a>擴充相依性圖表

您可以編寫代碼來創建和更新依賴關係關係圖，並根據 Visual Studio 中的依賴關係關係圖驗證程式代碼的結構。 您可以加入出現在圖表的捷徑 (操作) 功能表中的命令、自訂拖放軌跡，以及從文字範本存取圖層模型。 您可以將這些擴充功能封裝成 Visual Studio 整合擴充功能 (VSIX)，以及將這些整合擴充功能散發給其他 Visual Studio 使用者。

## <a name="requirements"></a>需求

您必須在想要開發圖層擴充功能的電腦上安裝下列項目：

- Visual Studio

- [視覺化工作室 SDK](../extensibility/visual-studio-sdk.md)

- 視覺化工作室建模 SDK

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

您必須在要運行圖層擴展的電腦上安裝合適的 Visual Studio 版本。 要查看哪些版本的 Visual Studio 支援依賴關係圖，請參閱[體系結構和建模工具的"版本"支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="see-also"></a>另請參閱

- [相依性圖表︰參考](../modeling/layer-diagrams-reference.md)
- [相依性圖表︰方針](../modeling/layer-diagrams-guidelines.md)
- [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)
- [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)
