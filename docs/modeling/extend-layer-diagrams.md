---
title: 擴充相依性圖表
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c164174b88ca9fdd815668084c1447e20de072c
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476559"
---
# <a name="extend-dependency-diagrams"></a>擴充相依性圖表

您可以撰寫程式碼來建立和更新相依性圖表，並驗證您的程式碼，針對 Visual Studio 中的相依性圖表的結構。 您可以加入出現在圖表的捷徑 (操作) 功能表中的命令、自訂拖放軌跡，以及從文字範本存取圖層模型。 您可以將這些擴充功能封裝成 Visual Studio 整合擴充功能 (VSIX)，以及將這些整合擴充功能散發給其他 Visual Studio 使用者。

## <a name="requirements"></a>需求

您必須在想要開發圖層擴充功能的電腦上安裝下列項目：

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- Modeling SDK for Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

您必須擁有 Visual Studio 您想要用來執行您的圖層擴充功能的電腦上安裝適當版本。 若要查看哪些版本的 Visual Studio 支援相依性圖表，請參閱[architecture and modeling tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="see-also"></a>另請參閱

- [相依性圖表中：參考](../modeling/layer-diagrams-reference.md)
- [相依性圖表中：方針](../modeling/layer-diagrams-guidelines.md)
- [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)
- [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)
